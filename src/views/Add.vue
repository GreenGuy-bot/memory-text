<template>
    <div>
        <p class="biaoti">标题</p>
        <input type="text" v-model="title" class="kuang">
        <p class="biaoti">内容</p>
        <textarea v-model="content" class="dakuang">{{content}}</textarea>
        <div class="btn" @click="add()" @mouseover="mouses($event)" @mouseout="outt">完成</div>
        <div class="quxiao" @click="cancel()" @mouseover="mouses($event)" @mouseout="outt2">取消</div>
    </div>
</template>

<script>
  import store from '@/store'

  export default {
    name: "Add",

    data() {
      return {
        title: '',
        content: '',
        nowTime: ''
      }
    },
    created() {
      this.nowTimes();
    },
    mounted() {
      this.nowTimes();
    },
    methods: {
      mouses: function ($event) {
        $event.currentTarget.className = "ao active"
      },
      outt($event) {
        $event.currentTarget.className = "btn"
      },
      outt2($event) {
        $event.currentTarget.className = "quxiao"
      },
      timeFormate(timeStamp) {
        let year = new Date(timeStamp).getFullYear();
        let month = new Date(timeStamp).getMonth() + 1 < 10 ? "0" + (new Date(timeStamp).getMonth() + 1) : new Date(timeStamp).getMonth() + 1;
        let date = new Date(timeStamp).getDate() < 10 ? "0" + new Date(timeStamp).getDate() : new Date(timeStamp).getDate();
        let hh = new Date(timeStamp).getHours() < 10 ? "0" + new Date(timeStamp).getHours() : new Date(timeStamp).getHours();
        let mm = new Date(timeStamp).getMinutes() < 10 ? "0" + new Date(timeStamp).getMinutes() : new Date(timeStamp).getMinutes();
        // let ss =new Date(timeStamp).getSeconds() < 10? "0" + new Date(timeStamp).getSeconds(): new Date(timeStamp).getSeconds();
        // return year + "年" + month + "月" + date +"日"+" "+hh+":"+mm ;
        this.nowTime = year + "年" + month + "月" + date + "日" + " " + hh + ":" + mm;
        // console.log(this.nowTime);
      },
// 定时器函数
      nowTimes() {
        this.timeFormate(new Date());
        setInterval(this.nowTimes, 30 * 1000);
      },
      cancel() {
        this.$router.push('/home/user')
      },
      add() {
        if (this.content !== '' && this.title !== '') {
          store.commit('addItem', {
            title: this.title,
            content: this.content
          })
          this.title = ''
          this.content = ''
          this.$store.commit('addTime', this.nowTime)
          this.$router.push('/home/list')
        } else {
          alert('标题或文本框为空！！')
        }
      }
    }
  }
</script>

<style scoped>
    .ao {
        margin-top: 37px;
        float: left;
        width: 177px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #ccc;
        color: #ffffff;
        font-weight: bold;
        text-align: center;
        line-height: 1.8em;
        box-shadow: 1px 2px 2px 2px darkgray inset;
    }

    .biaoti {
        padding-top: 20px;
        padding-left: 10px;
    }

    .kuang {
        width: 85%;
        margin-left: 12px;
        height: 27px;
        border-radius: 5px;
    }

    .dakuang {
        border-top-color: darkgray;
        border-left-color: darkgray;
        border-width: 2px;
        border-radius: 5px;
        margin-left: 12px;
        height: 370px;
        width: 85%;
    }

    .btn {
        margin-top: 37px;
        float: left;
        width: 177px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #42b983;
        color: #ffffff;
        font-weight: bold;
        text-align: center;
        line-height: 1.8em;
    }

    .quxiao {
        line-height: 1.8em;
        margin-top: 37px;
        float: left;
        width: 177px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #ffffff;
        color: #42b983;
        font-weight: bold;
        text-align: center;
        border-style: solid;
        border-color: #42b983;
        border-width: 1.5px;

    }
</style>
