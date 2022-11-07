# JS
JS

## 文档
- [dplayer自定义hls播放M3U8](https://www.cnblogs.com/ycc1/p/14042616.html)
- [4类javascript内存泄漏](https://jinlong.github.io/2016/05/01/4-Types-of-Memory-Leaks-in-JavaScript-and-How-to-Get-Rid-Of-Them/)

## 设备判定
```
if(/Android|webOS|iPhone|iPod|BlackBerry/i.test(navigator.userAgent)) {
    // 移动端操作
} else {
    // PC端操作
}
```

## 加解密算法
``` javascript
import CryptoJS from "crypto-js";
import sha256 from "sha256";
import md5 from "md5";
// const key = "cc88ddc9357ff461e08f047aedee692b";
// const iv = "81d7beac44a86f43";
// appkey和iv转换方法：
// var a = 'k89025cffyimgkcu';var b = a.split('');
// var c = [];b.forEach((item)=>{c.push(item.charCodeAt())});
// var d = c.join('_');
// console.log(d);
const appkey =
  "97_97_57_57_100_102_99_57_51_53_55_102_102_52_54_49_101_48_56_102_48_52_55_97_101_100_101_101_54_57_50_98"
    .split("_")
    .map((a) => String.fromCharCode(parseInt(a)))
    .join("");

const key = CryptoJS[
  String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)
][
  String.fromCharCode(85) +
  String.fromCharCode(116) +
  String.fromCharCode(102) +
  String.fromCharCode(56)
][`${String.fromCharCode(112)}arse`](
  "97_97_57_57_100_102_99_57_51_53_55_102_102_52_54_49_101_48_56_102_48_52_55_97_101_100_101_101_54_57_50_98"
    .split("_")
    .map((a) => String.fromCharCode(parseInt(a)))
    .join("")
);
const iv = CryptoJS[
  String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)
][
  String.fromCharCode(85) +
  String.fromCharCode(116) +
  String.fromCharCode(102) +
  String.fromCharCode(56)
][`${String.fromCharCode(112)}arse`](
  "107_56_57_48_50_53_99_102_102_121_105_109_103_107_99_117"
    .split("_")
    .map((a) => String.fromCharCode(parseInt(a)))
    .join("")
);
const media_key = CryptoJS[
  String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)
][
  String.fromCharCode(85) +
  String.fromCharCode(116) +
  String.fromCharCode(102) +
  String.fromCharCode(56)
][`${String.fromCharCode(112)}arse`](
  "102_53_100_57_54_53_100_102_55_53_51_51_54_50_55_48"
    .split("_")
    .map((a) => String.fromCharCode(parseInt(a)))
    .join("")
);
const media_iv = CryptoJS[
  String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)
][
  String.fromCharCode(85) +
  String.fromCharCode(116) +
  String.fromCharCode(102) +
  String.fromCharCode(56)
][`${String.fromCharCode(112)}arse`](
  "57_55_98_54_48_51_57_52_97_98_99_50_102_98_101_49"
    .split("_")
    .map((a) => String.fromCharCode(parseInt(a)))
    .join("")
);
//签名算法
function getSign(obj) {
  const keyValues = [];
  if (typeof obj.data !== "undefined") {
    keyValues.push(`client=${obj.client}`);
  }
  if (typeof obj.data !== "undefined") {
    keyValues.push(`data=${obj.data}`);
  }
  if (typeof obj.errcode !== "undefined") {
    keyValues.push(`errcode=${obj.errcode}`);
  }
  if (typeof obj.timestamp !== "undefined") {
    keyValues.push(`timestamp=${obj.timestamp}`);
  }
  const text = keyValues.join("&") + appkey;
  const sha256Text = sha256(text);
  const md5Text = md5(sha256Text);
  return md5Text;
}
// Hex '72_101_120'
// Utf8 '85_116_102_56'
// Base64 '66_97_115_101_54_52'
//解密方法
function Decrypt(word) {
  const encryptedHexStr =
    CryptoJS[
      String.fromCharCode(101) +
      String.fromCharCode(110) +
      String.fromCharCode(99)
    ][
      "72_101_120"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ][`${String.fromCharCode(112)}arse`](word);
  const srcs =
    CryptoJS[
      String.fromCharCode(101) +
      String.fromCharCode(110) +
      String.fromCharCode(99)
    ][
      "66_97_115_101_54_52"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ].stringify(encryptedHexStr);
  const decrypt = CryptoJS[
    String.fromCharCode(65) + String.fromCharCode(69) + String.fromCharCode(83)
  ][
    "100_101_99_114_121_112_116"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ](srcs, key, {
    iv,
    mode: CryptoJS[
      "109_111_100_101"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ][
      String.fromCharCode(67) +
      String.fromCharCode(70) +
      String.fromCharCode(66)
    ],
    padding:
      CryptoJS[`${String.fromCharCode(112)}ad`][
      `${String.fromCharCode(78)}o${String.fromCharCode(80)}adding`
      ],
  });
  const decryptedStr = decrypt.toString(
    CryptoJS[
    String.fromCharCode(101) +
    String.fromCharCode(110) +
    String.fromCharCode(99)
    ][
    String.fromCharCode(85) +
    String.fromCharCode(116) +
    String.fromCharCode(102) +
    String.fromCharCode(56)
    ]
  );
  return JSON[`${String.fromCharCode(112)}arse`](decryptedStr.toString());
}
function DecryptImage(word) {
  // const encryptedHexStr =
  //   CryptoJS[
  //     String.fromCharCode(101) +
  //     String.fromCharCode(110) +
  //     String.fromCharCode(99)
  //   ][
  //     "72_101_120"
  //       .split("_")
  //       .map((a) => String.fromCharCode(parseInt(a)))
  //       .join("")
  //   ][`${String.fromCharCode(112)}arse`](word);
  // const srcs =
  //   CryptoJS[
  //     String.fromCharCode(101) +
  //     String.fromCharCode(110) +
  //     String.fromCharCode(99)
  //   ][
  //     "66_97_115_101_54_52"
  //       .split("_")
  //       .map((a) => String.fromCharCode(parseInt(a)))
  //       .join("")
  //   ].stringify(encryptedHexStr);
  const decrypt = CryptoJS[
    String.fromCharCode(65) + String.fromCharCode(69) + String.fromCharCode(83)
  ][
    "100_101_99_114_121_112_116"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ](word, media_key, {
    iv: media_iv,
    mode: CryptoJS[
      "109_111_100_101"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ][
      String.fromCharCode(67) +
      String.fromCharCode(66) +
      String.fromCharCode(67)
    ],
    padding:
      CryptoJS[`${String.fromCharCode(112)}ad`][
      `${String.fromCharCode(78)}o${String.fromCharCode(80)}adding`
      ],
  });
  const decryptedStr = decrypt.toString(
    // CryptoJS[
    // String.fromCharCode(101) +
    // String.fromCharCode(110) +
    // String.fromCharCode(99)
    // ][
    // String.fromCharCode(85) +
    // String.fromCharCode(116) +
    // String.fromCharCode(102) +
    // String.fromCharCode(56)
    // ]
    CryptoJS.enc.Base64
  );
  return decryptedStr;
}

function DecryptVideo(word) {
  // const encryptedHexStr = CryptoJS[String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)].Utf8[`${String.fromCharCode(112)}arse`](word);
  // const srcs = CryptoJS[String.fromCharCode(101) + String.fromCharCode(110) + String.fromCharCode(99)][
  //     '66_97_115_101_54_52'
  //         .split('_')
  //         .map(a => String.fromCharCode(parseInt(a)))
  //         .join('')
  // ].stringify(encryptedHexStr);
  const decrypt = CryptoJS[
    String.fromCharCode(65) + String.fromCharCode(69) + String.fromCharCode(83)
  ][
    "100_101_99_114_121_112_116"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ](word, media_key, {
    iv: media_iv,
    mode: CryptoJS[
      "109_111_100_101"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ][
      String.fromCharCode(67) +
      String.fromCharCode(66) +
      String.fromCharCode(67)
    ],
    padding: CryptoJS[`${String.fromCharCode(112)}ad`].Pkcs7,
  });
  const decryptedStr = decrypt.toString(
    CryptoJS[
    String.fromCharCode(101) +
    String.fromCharCode(110) +
    String.fromCharCode(99)
    ][
    String.fromCharCode(85) +
    String.fromCharCode(116) +
    String.fromCharCode(102) +
    String.fromCharCode(56)
    ]
  );
  return decryptedStr;
}
//加密方法
function Encrypt(word) {
  const srcs =
    CryptoJS[
      String.fromCharCode(101) +
      String.fromCharCode(110) +
      String.fromCharCode(99)
    ][
      String.fromCharCode(85) +
      String.fromCharCode(116) +
      String.fromCharCode(102) +
      String.fromCharCode(56)
    ][`${String.fromCharCode(112)}arse`](word);
  const encrypted = CryptoJS[
    String.fromCharCode(65) + String.fromCharCode(69) + String.fromCharCode(83)
  ][
    "101_110_99_114_121_112_116"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ](srcs, key, {
    iv,
    mode: CryptoJS[
      "109_111_100_101"
        .split("_")
        .map((a) => String.fromCharCode(parseInt(a)))
        .join("")
    ][
      String.fromCharCode(67) +
      String.fromCharCode(70) +
      String.fromCharCode(66)
    ],
    padding:
      CryptoJS[`${String.fromCharCode(112)}ad`][
      `${String.fromCharCode(78)}o${String.fromCharCode(80)}adding`
      ],
  });
  const data = encrypted[
    "99_105_112_104_101_114_116_101_120_116"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ].toString()[
    "116_111_85_112_112_101_114_67_97_115_101"
      .split("_")
      .map((a) => String.fromCharCode(parseInt(a)))
      .join("")
  ]();
  const unix_t = new Date().getTime() / 1000;
  const timestamp = parseInt(unix_t.toString());
  const sign = getSign({ client: "pwa", data, timestamp });
  return { client: "pwa", sign, timestamp, data };
}
// eslint-disable-next-line no-multi-assign
const CryptoData = (window.CryptoData = {
  Decrypt,
  DecryptImage,
  DecryptVideo,
  Encrypt,
});
export default CryptoData;
```

## 播放器
- [视频播放器](https://aplayer.js.org/#/zh-Hans/?id=hls)

## socker使用方法
```javascript
IO.Socket socket = IO.io('http://localhost:3000',
  OptionBuilder()
      .setTransports(['websocket']) // for Flutter or Dart VM
      .setExtraHeaders({'foo': 'bar'}) // optional
      .build());
Socket socket = io('http://localhost:3000', 
    OptionBuilder()
      .setTransports(['websocket']) // for Flutter or Dart VM
      .disableAutoConnect()  // disable auto-connection
      .setExtraHeaders({'foo': 'bar'}) // optional
      .build()
  );
socket.connect();
socket.onConnect((_) {
    print('connect');
    socket.emit('msg', 'test');
  });
  socket.on('event', (data) => print(data));
  socket.onDisconnect((_) => print('disconnect'));
  socket.on('fromServer', (_) => print(_));
```