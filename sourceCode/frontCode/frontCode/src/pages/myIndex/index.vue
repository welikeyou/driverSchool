<template>
  <div class="body">
     <!-- <img @click="toUserInfo" id="user_icon" :src="userInfo.headImage"/>
      <img @click="toForum" id="forum_icon" :src="userInfo.headImage"/> -->
  <div class="userInfo">
   <div class="userName"> <open-data type="userNickName"></open-data></div>
     <open-data type="userAvatarUrl" class="userImg"></open-data>
  <!-- <img :src="userInfo.img" class="userImg"> -->
  </div> 
  <div class="timeTable">
     <input type="button" value="修改" @click="changeTime" class="btnStyle">
         <div>
           <div class="timeTableText">时间表</div>
      <div class="freeTimeBox">
         <div class="freeTimeBox1">
          <div
            v-for="item in timeList"
            :key="item"
            class="freeTimeDiv"
          >{{item}}</div>
        </div>
        <div class="freeTimeBox1">
         <div class="freeTimeDiv">上午</div>
          <div
            v-for="(item,index) in freeTime"
            :key="item"
            v-if="index%2==0"
            :class="{freeTimeDiv:!item.isChoosed,freeTimeDivChoosed:item.isChoosed}"
            id="freeTimeID"
          ></div>
        </div>
        <div class="freeTimeBox1">
          <div class="freeTimeDiv">下午</div>
          <div
            v-for="(item,index) in freeTime"
            :key="item"
            v-if="index%2==1"
            :class="{freeTimeDiv:!item.isChoosed,freeTimeDivChoosed:item.isChoosed}"
            id="freeTimeID"
          ></div>
        </div>
      </div>
    </div>      
  </div> 
 <myTabBar v-bind:in-home="true" v-bind:in-forum="false" v-bind:in-personal="false"></myTabBar>
  </div>
</template>
<style>
.body {
  background-color: white;
}
.userInfo{
  display: flex;
  flex-direction:row;
  width: 200rpx;
  height: 80rpx;
  position: relative;
  left: 550rpx;
  align-items: center;
  justify-content: space-around;
}
.userName{
  font-size:30rpx;
}
.userImg{
  width:80rpx;
  height: 80rpx;
  border-radius: 50%;
}
.timeTable{
  margin-top: 10rpx;
}
.timeTableText{
  position: relative;
  left: 40%;
  width: 150rpx;
}
.freeTimeDiv {
  width: 150rpx;
  height: 40rpx;
  margin: 30rpx auto;
  padding-top: 15rpx;
  text-align: center;
   border-radius: 10rpx;
}
.freeTimeDivChoosed {
  width: 150rpx;
  height: 40rpx;
  background-color: rgb(30, 190, 24);
  margin: 30rpx auto;
  padding-top: 15rpx;
  text-align: center;
  border-radius: 10rpx;
}
.notValide{
  width: 150rpx;
  height: 40rpx;
  background-color: rgb(36, 36, 36);
  margin: 30rpx auto;
  padding-top: 15rpx;
  text-align: center;
  border-radius: 10rpx;
}
.freeTimeBox {
  margin-top: 20rpx;
  display: flex;
  flex-direction: row;
}
.freeTimeBox1 {
  margin-left: 40rpx;
}
.btnStyle {
  /* width:140rpx;
  height: 70rpx;
  border-radius: 20rpx;
  font-size:30rpx;
  position: absolute;
  right:20rpx; */
  border-radius: 100rpx;
  font-size: 30rpx;
  width: 20%;
  color:rgb(0, 0, 0);
  background-color:white;
  border-style: solid;
  border-width: 2px;
  border-color: rgba(206, 206, 206, 0.774);
  position: absolute;
  right:20rpx;
}
</style>

<script>
import myTabBar from '@/components/myTabBar'
import {localUrl} from '../../config'
// 创建页面时必须暴露
export default {
    components: {
    myTabBar
  },
 name: 'home',
  data() {
    return {
      userInfo:{
        name:"",
        img:""
        
      },  
      freeTime: [{
                        "time": "周一上午",
                        "isChoosed": false,
                         "isChanged": false,
                         "isValided":true,
                        "id":0
                    },
                    {
                        "time": "周一下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":1
                    },
                    {
                        "time": "周二上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":2
                    },
                    {
                        "time": "周二下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":3
                    },
                    {
                        "time": "周三上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":4
                    },
                    {
                        "time": "周三下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":5
                    },
                    {
                        "time": "周四上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":6
                    },
                    {
                        "time": "周四下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":7
                        
                    },
                    {
                        "time": "周五上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":8
                    },
                    {
                        "time": "周五下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":9
                    },
                    {
                        "time": "周六上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":10
                    },
                    {
                        "time": "周六下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":11
                    },
                    {
                        "time": "周日上午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":12
                    },
                    {
                        "time": "周日下午",
                        "isChoosed": false,
                        "isChanged": false,
                         "isValided":true,
                        "id":13
                    }],   
      timeList:["","周一","周二","周三","周四","周五","周六","周日"]
    };
  },
  onLoad(){
   var _this=this;
      wx.request({
          url: `${localUrl}/GetArrange`,
        methods: 'GET',
        header: { 'content-type': 'application/json' },
        data: {
          'userID': 'll',
          
        },
        success: function (res) {
            for(var i=0; i<_this.freeTime.length;i++){
              _this.freeTime[i].isChoosed = false;
    
            }
            var arrangeTime = res.data
             console.log(arrangeTime)
            var date = arrangeTime.substring(0,arrangeTime.lastIndexOf("-"));
            var time = arrangeTime.substring(arrangeTime.lastIndexOf("-")+1);//获取上午还是下午，0表示上午，1表示下午
            var week = new Date(date).getDay();//获取星期
            var theIndex = (week-1)*2+Number(time);
            console.log(theIndex)
            _this.freeTime[theIndex].isChoosed = true
        },
        fail: function (err) {
          console.log(err)
        }
      })
             wx.request({
          url: `${localUrl}/GetTimeList`,
        methods: 'GET',
        header: { 'content-type': 'application/json' },
        data: {
          'userID': '0001',         
        },
        success: function (res) {
          var invalideTime = res.data;
          for(var i=0; i<invalideTime.length;i++){
            console.log(invalideTime[i]);
            var date = invalideTime[i].substring(0,invalideTime[i].lastIndexOf("-"));
            var time = invalideTime[i].substring(invalideTime[i].lastIndexOf("-")+1);//获取上午还是下午，0表示上午，1表示下午
            var week = new Date(date).getDay();//获取星期
            var theIndex = (week-1)*2+Number(time);
            console.log(theIndex)
            _this.freeTime[theIndex].isValided = false;

          }
           console.log(res.data);
        },
        fail: function (err) {
          console.log(err)
        }
      })
  },
  methods: {
    changeTime(){
       const url  = '../changeTime/main?freeTime='+JSON.stringify(this.freeTime)
      wx.navigateTo({url});
    },
  },
};
</script>

