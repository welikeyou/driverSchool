<template>
  <div class="body">
    <div class="title">{{msg}}欢迎你</div>
    <div><span style="color:red">*</span>请选择教练
      <div class="teacherDiv">
          <input type="radio" name="teacher" :value="item">
          {{teacherName}}
      </div>
    </div>
    <div><span style="color:red">*</span>请选择空闲时间
      <div class="freeTimeBox">
        <div class="freeTimeBox1">
          <div
            v-for="(item,index) in freeTime"
            :key="item"
            v-if="index%3==0"
            :class="{notValide:!item.isValided,freeTimeDiv:(item.isValided&&!item.isChoosed),freeTimeDivChoosed:(item.isChoosed&&item.isValided)}"
            id="freeTimeID"
            @click="chooseTime(item)"
          >{{item.time}}</div>
        </div>
        <div class="freeTimeBox1">
          <div
            v-for="(item,index) in freeTime"
            :key="item"
            v-if="index%3==1"
            :class="{notValide:!item.isValided,freeTimeDiv:(item.isValided&&!item.isChoosed),freeTimeDivChoosed:(item.isChoosed&&item.isValided)}"
            id="freeTimeID"
            @click="chooseTime(item)"
          >{{item.time}}</div>
        </div>
        <div class="freeTimeBox1">
          <div
            v-for="(item,index) in freeTime"
            :key="item"
            v-if="index%3==2"
            :class="{notValide:!item.isValided,freeTimeDiv:(item.isValided&&!item.isChoosed),freeTimeDivChoosed:(item.isChoosed&&item.isValided)}"
            id="freeTimeID"
            @click="chooseTime(item)"
          >{{item.time}}</div>
        </div>
      </div>
    </div>
    <div>
     <span style="color:red"> *</span>请填写考试时间 
    <input type="text" id="testTime" class="testDiv" placeholder="请输入考试时间"  v-model="examTime"> 
    </div>
    <button class="btnStyle" @click="submitIfo">提交</button>
  </div>
</template>
<style>
.body {
  background-color: white;
}
.title {
  text-align: center;
  margin-bottom: 20rpx;
}

.teacherDiv {
  margin-top: 20rpx;
  margin-bottom: 20rpx;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
.freeTimeDiv {
  width: 200rpx;
  height: 60rpx;
  background-color:rgb(247, 217, 48);
    color:#ffffff;
  margin: 30rpx auto;
  padding-top: 15rpx;
  text-align: center;
   border-radius: 10rpx;
}
.freeTimeDivChoosed {
  width: 200rpx;
  height: 60rpx;
  background-color: rgb(30, 190, 24);
    color:#ffffff;
  margin: 30rpx auto;
  padding-top: 15rpx;
  text-align: center;
  border-radius: 10rpx;
}
.notValide{
  width: 200rpx;
  height: 60rpx;
  background-color: rgba(220, 220, 220,0.4);
  color:#888888;
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
.testDiv{
  background-color: aliceblue;
  padding-left:20rpx;
  height:70rpx;
  margin-top:10rpx;
}
.btnStyle {
  /* margin-top: 25rpx;
  background-color:  rgb(30, 190, 24); */
  border-radius: 80rpx;
  margin: 50rpx 50rpx;
  font-size: 35rpx;
  color:ghostwhite;
  background-color:rgba(24, 190, 18, 0.966);
}
</style>

<script>
// 创建页面时必须暴露
import {localUrl} from '../../config'
export default {
  data() {
    return {
      msg: "",
      examTime:"",
      teachers: [],
      teacherId:'',
      teacherName:'',
      schoolId:'',
      schoolInfo:'',
      freeTime: [{
                        "time": "周一上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":0
                    },
                    {
                        "time": "周一下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":1
                    },
                    {
                        "time": "周二上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":2
                    },
                    {
                        "time": "周二下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":3
                    },
                    {
                        "time": "周三上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":4
                    },
                    {
                        "time": "周三下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":5
                    },
                    {
                        "time": "周四上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":6
                    },
                    {
                        "time": "周四下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":7
                        
                    },
                    {
                        "time": "周五上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":8
                    },
                    {
                        "time": "周五下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":9
                    },
                    {
                        "time": "周六上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":10
                    },
                    {
                        "time": "周六下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":11
                    },
                    {
                        "time": "周日上午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":12
                    },
                    {
                        "time": "周日下午",
                        "isChoosed": false,
                        "isValided":true,
                        "id":13
                    }]
    };
  },
    // 生命周期函数,mpvue除了vue本身的生命周期外还兼容了小程序的生命周期
    onLoad(option) {
      console.log(option)
      var _this=this;
      //获取驾校信息
      wx.request({
          url: `${localUrl}/GetSchoolInfo`,
        methods: 'GET',
        header: { 'content-type': 'application/json' },
        data: {
          'userId': 'll',
          'identyCode':option.identyCode
          
        },
        success: function (res) {
          var schoolInfo = res.data;
          // console.log(res.data);
          _this.schoolId = schoolInfo.schoolId;
          _this.msg=schoolInfo.schoolName;
          _this.teacherId=schoolInfo.teacherId;
          _this.teacherName=schoolInfo.teacherName;
        },
        fail: function (err) {
          console.log(err)
        }
      })
      //获取可用时间
      wx.request({
          url: `${localUrl}/GetTimeList`,
        methods: 'GET',
        header: { 'content-type': 'application/json' },
        data: {
          'userID': 'll',         
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
    chooseTime(item) {
      if(item.isValided){
      item.isChoosed = !item.isChoosed;
      console.log(item.isChoosed);
      }
      else{
          var toastText = '时间不可用';
          wx.showToast({
            title: toastText,
            icon: '',
            duration: 2000
          });
      }

    },
    submitIfo(){
    /*  var _this=this;
    //  _this.testTime = document.getElementById('testTime').value;
       wx.navigateTo({url:'../myIndex/main'})
      wx.request({
          url: 'http://localhost:8080/api/info',
        methods: 'GET',
        header: { 'content-type': 'application/json' },
        data: {
          'teacherId': '123',
          'freeTime':_this.freeTime,
          'testTime':""
        },
        success: function (res) {
        
          console.log("提交成功");
         
        },
        fail: function (err) {
          console.log(err)
        }
      })

    }*/
    console.log(this.examTime)
     var that = this;
      wx.request({
      url: `${localUrl}/SetUserInfo`,
      method: 'GET',
      data:{
        userId:'ll',
        userName:'兰蝶',
        userSchool:that.schoolId,
        userTeacher:that.teacherId,
        examTime:that.examTime

      },
      header: {
        'content-type': 'application/json' // 默认值
      },
      success: function (res) {
        console.log(res.data)//打印到控制台
        var list = res.data;
        if (list == null) {
          var toastText = '数据获取失败';
          wx.showToast({
            title: toastText,
            icon: '',
            duration: 2000
          });
        } 
      },
    });   
      wx.request({
      url: `${localUrl}/NewArrange`,
      method: 'GET',
      data:{
        userID:'ll',
        arrangeDate:'2019-5-21',
        arrangeTimeIndex:'1'
      },
      header: {
        'content-type': 'application/json' // 默认值
      },
      success: function (res) {
        console.log(res.data)//打印到控制台
        var list = res.data;
        if (list == null) {
          var toastText = '数据获取失败';
          wx.showToast({
            title: toastText,
            icon: '',
            duration: 2000
          });
        } else {
          const url = '../myIndex/main';
          wx.navigateTo({url});
        }
      },
    });

  }
 }
}
</script>

