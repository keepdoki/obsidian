## 全面屏兼容

```javascript

// /pages.json

{

  ...

  "globalStyle": {

    ...

    "navigationStyle": "custom",

  }

}

```

  

```javascript

// /App.vue

<style>

  /*每个页面公共css */

  page {

    padding-bottom: constant(safe-area-inset-bottom);

    padding-bottom: env(safe-area-inset-bottom);

  }

  .page-content {

    padding-top: var(--status-bar-height);

  }

  .page-content.have-bar {

    padding-top: calc(88rpx + var(--status-bar-height));

  }

  .bg {

    background-size: contain;

    background-repeat: no-repeat;

    background-position: center;

  }

  button {

    margin: 0;

    padding: 0;

    border: none;

    outline: none;

  }

  button::after {

    border: none;

  }

</style>

```

  

### 自定义TabBar组件

- [链接](https://uniapp.dcloud.net.cn/component/custom-tab-bar.html#custom-tab-bar)

  

1. pages.json 设置TabBar页面

    ```javascript

    {

    ...

      "tabBar": {

        "list": [

          {

            "pagePath": "pages/index/index"

          },

          {

            "pagePath": "pages/my/index"

          }

        ]

      }

    }    

    ```

2. 编写自定义TabBar

```javascript

<template>

  <view class="bottom">

    <view class="tabbar-item" v-for="(item, index) in list" :key="index" @click="tabbarChange(item.pagePath)">

      <image :src="index === current ? item.selectedIconPath : item.iconPath" class="icon"></image>

      <text class="text" :class="{'active': index === current}">{{ item.text }}</text>

    </view>

  </view>

</template>

  

<script>

  export default {

    props: {

      current: {

        type: Number,

        default: 0

      },

    },

  data() {

    return {

        list: [

          {

            "pagePath": "/pages/index/index",

            "iconPath": "/static/icon_tabBar-home.png",

            "selectedIconPath": "/static/icon_tabBar-home--active.png",

            "text": "首页",

          },

          {

            "pagePath": "/pages/my/index",

            "iconPath": "/static/icon_tabBar-my.png",

            "selectedIconPath": "/static/icon_tabBar-my--active.png",

            "text": "我的",

          }

        ]

    }

  },

  methods: {

      tabbarChange(path) {

        uni.switchTab({

          url: path,

        })

      }

  }

  }

</script>

  

<style lang="scss" scoped>

  .bottom {

    position: fixed;

    right: 0;

    bottom: 0;

    left: 0;

    display: flex;

    justify-content: center;

    align-items: center;

    background: #FFFFFF;

    border-top: 2rpx solid rgba(204, 204, 204, 0.2);

    padding-bottom: constant(safe-area-inset-bottom);

    padding-bottom: env(safe-area-inset-bottom);

  }

  .tabbar-item {

    flex: 1;

    height: 96rpx;

    display: flex;

    flex-direction: column;

    align-items: center;

    justify-content: center;

    box-sizing: border-box;

    padding-top: 6rpx;

    .icon {

      width: 48rpx;

      height: 48rpx;

    }

    .text {

      font-size: 22rpx;

      font-family: 'PingFangSC-Regular', 'PingFang SC', sans-serif;

      font-weight: 400;

      color: #59606F;

      line-height: 32rpx;

    }

    .text.active {

      color: #6275FF;

    }

  }

</style>

  

```

3. 在TabBar页设置, 隐藏原生的TabBar

```javascript

<template>

...

  <!--根据顺序对应，从0开始-->

  <view-tabbar :current="0"></view-tabbar>

<template>.

<script>

...

import CustomTabBar from '@/components/CustomTabBar.vue'

...

export default {

  components: {

    ...

    'view-tabbar' : CustomTabBar

  },

  ...

  onShow(){

    uni.hideTabBar({

      animation: false

    })

  }

}

  

</script>

```