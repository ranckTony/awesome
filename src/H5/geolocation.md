# geolocation

geolocation 获取设备定位信息的api

基本用法

```javascript

  function success (position) {
    // 经度 纬度 海拔 
  }

  function error (e) {
    
  }

  navigator.geolocation.getCurrentPosition(success, error, {
    // 指示浏览器获取高精度的位置，默认为false
    enableHighAccuracy: true,
    // 指定获取地理位置的超时时间，默认不限时，单位为毫秒
    timeout: 5000,
    // 最长有效期，在重复获取地理位置时，此参数指定多久再次获取位置。
    maximumAge: 3000
  });
```
