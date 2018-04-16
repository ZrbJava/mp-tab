##效果图：

![效果图](img/preview.gif)

##原码如下
```html
<!--index.wxml-->  
<view class="swiper-tab" >  
    <view bindtap="swithNav" wx:for="{{tabCont}}" wx:key="item.index" class="swiper-tab-list {{currentTab==item.index?'active':''}}" data-current='{{item.index}}' >{{item.title}}</view>  
</view>  
<swiper class="swiper-box" current="{{currentTab}}" duration="300" style="height:400px" bindchange="GetCurrentTab" data-current='6' >  
    <swiper-item wx:for="{{tabCont}}" wx:key="item.index">  
      <image src='{{item.pic}}'></image>
      <view>{{item.title}}</view>
    </swiper-item>  
</swiper>  
```

```css
/**index.wxss**/


.swiper-tab {
  line-height: 80rpx;
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.swiper-tab-list {
  font-size: 30rpx;
  color: #777;
  text-align: center;
}

.active {
  color: #da7c0c;
  border-bottom: 5rpx solid #da7c0c;
}

.swiper-box {
  display: block;
  height: 100%;
  width: 100%;
  overflow: hidden;
}

.swiper-box view {
  text-align: center;
}

image {
  width: 100%;
}

```
```js
/*
*index.js
*/
Page({

  /**
   * 页面的初始数据
   */
  data: {
    currentTab:0,
    tabCont: [{ "title": "tab1", "pic": "../../img/1.jpg", "index": "0" }, { "title": "tab2", "pic": "../../img/2.jpg", "index": "1" }, { "title": "tab3", "pic": "../../img/3.jpg", "index": "2" }, { "title": "tab4", "pic": "../../img/2.jpg", "index": "3" }, { "title": "tab5", "pic": "../../img/2.jpg", "index": "4" }, { "title": "tab6", "pic": "../../img/2.jpg", "index": "5" }, { "title": "tab7", "pic": "../../img/2.jpg", "index": "6" }, { "title": "tab8", "pic": "../../img/2.jpg", "index": "7" }, { "title": "tab9", "pic": "../../img/2.jpg", "index": "8" }],
  },

  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
    
  },

  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function () {
    
  },

  /**
   * 生命周期函数--监听页面显示
   */
  onShow: function () {
    
  },

  /**
   * 生命周期函数--监听页面隐藏
   */
  onHide: function () {
    
  },

  /**
   * 生命周期函数--监听页面卸载
   */
  onUnload: function () {
    
  },

  /**
   * 页面相关事件处理函数--监听用户下拉动作
   */
  onPullDownRefresh: function () {
    
  },

  /**
   * 页面上拉触底事件的处理函数
   */
  onReachBottom: function () {
    
  },

  /**
   * 用户点击右上角分享
   */
  onShareAppMessage: function () {
    
  },
  // swiper滑动时触发bindchange事件，获取事件对象e获取当前所在滑块的 index，并将其更新至data的currentTab中，视图渲染通过判断currentTab的让对应的tab hover。
  GetCurrentTab:function(e){
    console.log(e.detail.current);
    var that = this;
    this.setData({
      currentTab:e.detail.current
    });
    // console.log("11111"+this.data.currentTab);
  },
  swithNav:function(e){
    var that = this;
   that.setData({
     currentTab:e.target.dataset.current
   });

  }
})
```