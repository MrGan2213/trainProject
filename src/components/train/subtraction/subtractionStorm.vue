<template>
  <div class="subtraction">
    <span class="surplusTime">{{surplusTime}}</span>
    <div id="divMain" ref="main" style="position: absolute;width:64%;height:88%;left:4%;top:5%;">
    </div>
    <div class="subcalc" style="">
      <div style="width: 75%;height: 18.8%;margin: 16.5% 11% 2.5% 11%;">
        <span style="font-size:40px;font-weight: bolder;float: right;margin-right:2%;position: relative;top:50%;transform:translateY(-50%);">{{result}}</span>
      </div>
      <div style="width: 75.5%;height: 56.5%;margin: 0% 10.5%;">
        <div style="width: 100%;height: 50%;">
          <div style="width:75%;height: 100%;float: left;">
            <div @click="inputNumber(7)" style="width: 31%;height: 45%;float: left;margin-right:3.5%;">
              <img src="@/assets/subtraction/num7.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(8)" style="width: 31%;height: 45%;float: left;margin-right: 3.5%;">
              <img src="@/assets/subtraction/num8.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(9)" style="width: 31%;height: 45%;float: left;margin-right: 0%">
              <img src="@/assets/subtraction/num9.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(4)" style="width: 31%;height: 45%;float: left;margin:4% 3.5% 0% 0%">
              <img src="@/assets/subtraction/num4.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(5)" style="width: 31%;height: 45%; solid;float: left;margin:4% 3.5% 0 0">
              <img src="@/assets/subtraction/num5.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(6)" style="width: 31%;height: 45%; solid;float: left;margin-top: 4%">
              <img src="@/assets/subtraction/num6.png" style="height: 100%;width: 100%;" />
            </div>
          </div>
          <div @click="doClear" style="width: 23%;height: 97%;float: left;margin-left:2% ;">
            <img src="@/assets/subtraction/btnClear.png" style="height: 100%;width: 100%;" />
          </div>
        </div>
        <div style="width:100%;height:49%;margin-top:1% ;">
          <div style="width:75%;height: 100%;float: left;z-index: 9999;position: relative;">
            <div @click="inputNumber(1)" style="width: 31%;height: 45%;float: left;margin-right:3.5%;">
              <img src="@/assets/subtraction/num1.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(2)" style="width: 31%;height: 45%;float: left;margin-right: 3.5%;">
              <img src="@/assets/subtraction/num2.png" style="height: 100%;width: 100%;" />
            </div>
            <div @click="inputNumber(3)" style="width: 31%;height: 45%;float: left;margin-right: 0%;z-index: 9999;">
              <img src="@/assets/subtraction/num3.png" style="height: 100%;width: 100%;z-index: 9999;" />
            </div>
            <div @click="inputNumber(0)" style="width:82%;height: 45%;float: left;margin:4% 3.5% 0% 0%">
              <img src="@/assets/subtraction/num0.png" style="height: 100%;width: 100%;" />
            </div>
          </div>
          <div @click="checkItem" style="width: 26%;height: 100%;float: left;margin-left:2%;">
            <img src="@/assets/subtraction/btnConfirm.png" style="height: 27%;width:28%; position: absolute;right:14%;bottom:11%;z-index: 1;" />
          </div>
        </div>
      </div>
    </div>
    <img v-if="isReady" src="@/assets/subtraction/ready.png" style="width: 100%;height: 100%;" />
    <div class="divResult" v-show="isFinish">
      <span style="position: absolute;left: 52%;top:42.5%;color: #357dd3;font-size: 40px;font-weight: bolder;">1</span>
      <span style="position: absolute;left: 52%;top: 50%;color:#357dd3;font-size: 40px;font-weight: bolder;">{{correctNumber}}</span>
      <span style="position: absolute;left: 52%;top: 57%;color:#357dd3;font-size:40px;font-weight:bolder;">{{accuracy}}%</span>
      <span style="position: absolute;left: 47%;top: 67%;color:#d7112f;font-size:60px;font-weight:700;">{{Math.round(correctNumber*10.5)}}分</span>
      <img style="position: absolute;left: 44%;bottom:2%;width: 12.5%;height: 10%;" src="@/assets/btnContinu.png"
        @click="readyGo" />
    </div>
  </div>
</template>

<script>
  import Vue from 'vue'
  /* import boatImg from "@/assets/subtraction/boat.png"*/
  import colors from "@/assets/subtraction/clors.png"
  import {
    randonArr,
    randomLimit,
    getRandomArr,
    randomNumBoth,
  } from '@/utils/common.js'
  export default {
    computed: {
      accuracy: function() {
        if (this.totalAnswerNumber === 0) return 0;
        return (this.correctNumber / this.totalAnswerNumber).toFixed(2) * 100;
      }
    },
    mounted() {
      /* this.boatHeight=this.$refs.boat[0].offsetHeight; */
      /* console.log(this.smashImgH)
       this.mainHeight=parseInt(this.mainHeight)-parseInt(this.boatHeight); */
      this.readyGo();
      //this.intervalTimer();
      //this.startBoat();
      //his.create();
      /* this.boatLeft=randomNumBoth(0,91.6,1);
      var dd=getRandomArr(this.boatColors,1);
      console.log(dd); */
    },
    data() {
      return {
        totalDuration: 200, //计时器总时长(秒)
        surplusTime: 200, //当前剩余时长
        isTimeout: false, //是否时间已到
        isFinish: false, //是否答题结束
        isReady: false, //是否准备开始
        readyTime: 1000, //准备时长毫秒
        totalAnswerNumber: 0,
        correctNumber: 0,
        intervalTime: null,
        interverBoat: null,
        result: '0',
        mainHeight: 0,
        boatHeight: 0,
        marginTopH: 0,
        boatInterval: null,
        /* boatStatusImg: boatImg,
        boatSmashImg: boatSmash, */
        isSmash: false,
        downSpeed: 2, //下降速度 px
        downSpanTime: 100, //多久下降一次
        boatLeft: 0,
        results: [],
        imgs: require("@/assets/subtraction/clors.png"),
        boatColors: ['boat_colors', 'boat_blue', 'boat_yellow'], //气球颜色，随机
        currentClass: '',
      }
    },
    methods: {
      intervalTimer() {
        this.surplusTime = this.totalDuration;
        this.isFinish = false;
        this.result = '0';
        this.results = [];
        this.totalAnswerNumber = 0;
        this.correctNumber = 0;
        this.isTimeout = false;
        this.mainHeight = this.$refs.main.offsetHeight;
        clearInterval(this.interverBoat)
        // 计时器为空，操作
        if (this.intervalTime != null) return;
        this.intervalTime = setInterval(() => {
          if (this.surplusTime > 0) {
            this.surplusTime = this.surplusTime - 1;
          } else {
            this.isTimeout = true;
            this.isFinish = true;
            clearInterval(this.intervalTime);
            this.intervalTime = null;
            this.removeBoat();
          }
        }, 1000)
      },
      inputNumber(val) {
        if (this.result.length > 6) return;
        if (parseInt(this.result) <= 0 && val === 0) {
          this.result = "0";
        } else {
          this.result = this.result == '0' ? val : this.result.toString() + val.toString();
        }
      },
      doClear() {
        this.result = this.result.toString().substring(0, this.result.length - 1)
        if (this.result.length <= 0) {
          this.result = "0";
        }
      },
      createBoat() {
        var topH = 0;
        var left = randomNumBoth(0, 90, 1)[0];
        var domClassName = getRandomArr(this.boatColors, 1)[0];
        //is.currentClass='boat '+domClassName;
        var nums = randomNumBoth(1, 15, 2);
        var num1 = nums[0];
        var num2 = nums[1];

        var maxNum = 0;
        var minNum = 0;
        if (num1 >= num2) {
          maxNum = num1;
          minNum = num2;
        } else {
          maxNum = num2;
          minNum = num1;
        }
        var result = maxNum - minNum;
        this.results.push(result);
        var divBoat = document.createElement('div');
        divBoat.className = "subboat " + domClassName;
        divBoat.style.left = left + '%';
        divBoat.style.top = topH + '%';
        divBoat.id = 'divBoat' + result;
        var spans = document.createElement('span');
        divBoat.appendChild(spans);
        spans.innerText = maxNum + '-' + minNum;
        var divSmash = document.createElement('div');
        divSmash.className = "subboatSmash";
        divSmash.style.marginLeft = left + '%';
        divSmash.style.backgroundColor = '#00FFFF';
        divSmash.style.display = 'none';
        divSmash.id = 'divSmash' + result;
        document.getElementById("divMain").appendChild(divBoat);
        document.getElementById("divMain").appendChild(divSmash);
        var boatH = document.getElementsByClassName(domClassName)[0].offsetHeight;
        this.interverBoat = setInterval(() => {
          var currentH = topH + this.downSpeed;
          if (currentH+20 < (this.mainHeight - boatH)) {
            topH = currentH;
            divBoat.style.top = topH + 'px';
          } else {
            this.isSmash = true;
            divBoat.remove();
            divSmash.style.display = 'block';
            this.removeSmash(divSmash);
            for (var i = 0; i < this.results.length; i++) {
              if (this.results[i] == result) {
                this.results.splice(i, 1);
                break;
              }
            }
            clearInterval(this.interverBoat)
            if (!this.isTimeout)
              this.createBoat();
          }
        }, this.downSpanTime);
      },
      removeSmash(dom) {
        setTimeout(() => {
          dom.remove();
        }, 500);
      },
      removeBoat() {
        var boats = document.querySelector(".subboat");
        if (boats != null) boats.remove()

        /* boats.forEach(function(item){
          item.remove();
        }) */
      },
      checkItem() {
        var isCorrect = this.results.indexOf(parseInt(this.result)) > -1;
        this.playAudio(isCorrect)
        this.totalAnswerNumber++;
        if (isCorrect) {
          this.correctNumber++;
          document.getElementById('divBoat' + this.result).remove();
          document.getElementById('divSmash' + this.result).remove();
          clearInterval(this.interverBoat);

          if (!this.isTimeout)
            this.createBoat()
          else
            this.isFinish = true;
        } else {

        }
        this.result = '0';
      },
      readyGo() {
        this.removeBoat();
        this.isReady = true;
        this.isFinish = false;
        this.isTimeout = false;
        setTimeout(() => {
          this.isReady = false;
          this.intervalTimer();
          this.createBoat();
        }, this.readyTime);
      },

    },
    beforeDestroy() {
      this.removeBoat();
      clearInterval(this.interverBoat);
      this.interverBoat = null;
    }
  }
</script>

<style>
  .subtraction {
    width: 100%;
    height: 100vh;
    /* position: fixed; */
    position: relative;
    background-image: url(../../../assets/subtraction/bg.jpg);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    background-position: center;
    -moz-background-size: 100% 100%;
  }

  .subtraction .surplusTime {
    position: absolute;
    right: 14%;
    top: 0%;
    font-weight: bolder;
    font-size: 25px;
  }

  .subcalc {
    position: absolute;
    width: 20.4%;
    height: 55.9%;
    right: 6%;
    bottom: 22%;
    background-image: url(../../../assets/subtraction/calculator.png);
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }

  .boat_colors {
    position: absolute;
    top: 0px;
    /* left:91.6%; */
    width: 6.5%;
    height: 12%;
    background-image: url(../../../assets/subtraction/clors.png);
    background-size: cover;
  }

  .boat_blue {
    position: absolute;
    top: 0px;
    /* left:91.6%; */
    width: 6.5%;
    height: 12%;
    background-image: url(../../../assets/subtraction/blue.png);
    background-size: cover;
  }

  .boat_yellow {
    position: absolute;
    top: 0px;
    /* left:91.6%; */
    width: 6.5%;
    height: 12%;
    background-image: url(../../../assets/subtraction/yellow.png);
    background-size: cover;
  }

  .subboatSmash {
    width: 15%;
    height: 5%;
    margin-top: 60%;
    background-image: url(../../../assets/subtraction/boatSmash1.png);
    background-size: cover;
  }

  .subboat {
    text-align: center;
  }

  .subboat span {
    font-size: 14px;
    font-weight: bold;
    position: absolute;
    top: 28%;
    left: 18%;
    margin: 0 auto;
  }

  .divResult {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0px;
    left: 0px;
    background-image: url(../../../assets/subtraction/result.png);
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center, center;
    z-index: 9999;
  }
</style>
