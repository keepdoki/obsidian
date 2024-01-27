```javascript

//ASCII码转16进制

function strToHexCharCode(str) {

  if (str === "") {

    return "";

  } else {

    const hexCharCode = [];

    hexCharCode.push("0x");

    for (let i = 0; i < str.length; i++) {

        hexCharCode.push((str.charCodeAt(i)).toString(16));

    }

    return hexCharCode.join("").toUpperCase();

  }

}

//十六进制转ASCII码

function hexCharCodeToStr(hexCharCodeStr) {

  const trimedStr = hexCharCodeStr.trim();

  const rawStr = trimedStr.substr(0, 2).toLowerCase() === "0x" ? trimedStr.substr(2) : trimedStr;

  const len = rawStr.length;

  if (len % 2 !== 0) {

      return "";

  }

  let curCharCode;

  const resultStr = [];

  for (var i = 0; i < len; i = i + 2) {

      curCharCode = parseInt(rawStr.substr(i, 2), 16);

      resultStr.push(String.fromCharCode(curCharCode));

  }

  return resultStr.join("");

}

```

## 下载文件

```javascript

// 通过a标签下载

function downloadFromLink(link, fileName = '') {

  return new Promise((resolve, reject) => {

    try {

      const a = document.createElement('a');

      const body = document.querySelector('body');

      a.href = link;

      a.style.display = 'none';

      if (fileName) {

        a.download = fileName;

      }

      body.appendChild(a);

      a.click();

      body.removeChild(a);

      window.URL.revokeObjectURL(a.href);

      resolve();

    } catch {

      reject();

    }

  });

}

&nbsp;

// 通过http下载blob, 使用URL.createObjectURL转成link,再通过a标签下载

function httpGetBlob(url) {

  return new Promise((resolve, reject) => {

    const xhr = new XMLHttpRequest();

    xhr.open('GET', url, true);

    xhr.addEventListener(

      'progress',

      (evt) => {

        if (evt.lengthComputable) {

          const percentComplete = evt.loaded / evt.total;

          // percentage是当前下载进度，可自行处理

          const percentage = percentComplete * 100;

          console.log('当前下载进度', percentage);

        }

      },

      false

    );

    xhr.responseType = 'blob';

    xhr.onload = () => {

      if (xhr.status === 200) {

        let fileName = '';

        try {

          const dis = xhr.getResponseHeader("Content-Disposition");

          fileName = dis.split(`attachment;filename*=utf-8''`)[1];

        } catch {

          console.log('获取名称失败');

        }

        resolve({ blob: xhr.response, fileName: decodeURIComponent(fileName) });

      } else {

        reject(xhr)

      }

    };

    xhr.send();

  })

}

```

  

## 页面加载完显示

  

```javascript

document.onreadystatechange = function () {

  if (document.readyState == "complete") {

    document.body.style.display = "block";

  } else {

    document.body.style.display = "none";

  };

};

```

  

## 半角、全角的判断及转化

  

```javascript

// 判断

const str="中文;；ａ"    

alert(str.match(/[\u0000-\u00ff]/g))     //半角  

alert(str.match(/[\u4e00-\u9fa5]/g))     //中文  

alert(str.match(/[\uff00-\uffff]/g))     //全角

&nbsp;

// 半角转全角

function ToDBC(txtstring) {

    var tmp = "";

    for(var i=0;i<txtstring.length;i++{

        if(txtstring.charCodeAt(i)==32){

            tmp= tmp+ String.fromCharCode(12288);

        }

        if(txtstring.charCodeAt(i)<127){

            tmp=tmp+String.fromCharCode(txtstring.charCodeAt(i)+65248);

        }

    }

    return tmp;

}

&nbsp;

// 全角转半角

function ToCDB(str) {

    var tmp = "";

    for(var i=0;i<str.length;i++){

        if (str.charCodeAt(i) == 12288){

            tmp += String.fromCharCode(str.charCodeAt(i)-12256);

            continue;

        }

        if(str.charCodeAt(i) > 65280 && str.charCodeAt(i) < 65375){

            tmp += String.fromCharCode(str.charCodeAt(i)-65248);

        }

        else{

            tmp += String.fromCharCode(str.charCodeAt(i));

        }

    }

    return tmp

}

```

  

## 快速获取年月日时分秒的写法

  

```javascript

new Date(+new Date() + 8 * 3600 * 1000).toJSON().substr(0, 16).replace('T', ' ')

```

```javascript
// 字符串替换
replacepos(text,start,stop,replacetext) {
  return text.substring(0,start)+replacetext+text.substring(stop);
}
// 二进制转16进制
binhex(bin, byte = 1) {
  let pre = '';
  for (let i = 0; i < (byte * 2); i ++) {
    pre = pre + '0';
  }
  return (pre + (parseInt(bin, 2).toString(16))).substr(-(byte*2)).toUpperCase();
}
// 十进制转16进制
hex16bin(hex, byte = 1) {
  let pre = '';
  for (let i = 0; i < (byte * 2); i ++) {
    pre = pre + '0';
  }
  return (pre + hex.toString(16)).substr(-(byte*2)).toUpperCase();
}
// 16进制转10进制
hex2bin(hex, byte = 1){
  let pre = '';
  for (let i = 0; i < (byte * 2); i ++) {
    pre = pre + '0000';
  }
  return (pre + (parseInt(hex, 16)).toString(2)).substr(-8 * byte);
}
//十六进制转ASCII码
hexCharCodeToStr(hexCharCodeStr) {
  const trimedStr = hexCharCodeStr.trim();
  const rawStr = trimedStr.substr(0, 2).toLowerCase() === "0x" ? trimedStr.substr(2) : trimedStr;
  const len = rawStr.length;
  if (len % 2 !== 0) {
    return "";
  }
  let curCharCode;
  const resultStr = [];
  for (var i = 0; i < len; i = i + 2) {
    curCharCode = parseInt(rawStr.substr(i, 2), 16);
    resultStr.push(String.fromCharCode(curCharCode));
  }
  return resultStr.join("");
}
// 字符串分段截取成数组
sliceStr(str, len) {
  const list = [];
  const num = Math.ceil(str.length / len);
  for (let i = 0; i < num; i ++) {
    const value = '' + str.slice(i * len, (i + 1) * len);
    list.push(value);
  }
  return list;
}
// 异或运算
getSum(list) {
  let total = 0;
  for (let i = 0; i < list.length; i ++) {
    total = total + parseInt(list[i], 16);
  }
  return total;
}
```