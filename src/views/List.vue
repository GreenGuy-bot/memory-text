<template>
    <div>
        <div v-show="show"><h5>这里空空如也~</h5></div>
        <ul>
            <li v-for="(item,index) in pagelists" :key="index">标题:{{item.title}}<br/>内容:{{item.content}}<br/>
                {{gettime[index]}}
                <button class="sss" @click='pagelists.splice(index, 1)&&gettime.splice(index, 1)'>删除</button>
            </li>
        </ul>
        <div class="taozi">
            <div class="fanhui" @click="fanhui()">返回登录界面</div>
        </div>

    </div>
</template>

<script>
  import store from '@/store'

  export default {

    name: "List",
    data() {
      return {
        listt: []
      }
    },
    methods: {
      fanhui() {
        this.$router.push('/')
      },
    },
    computed: {
      pagelists: function () {
        return store.state.lists
      },
      show(){
         return store.state.lists.length <= 0;//判断数组是否为空的简化写法，是否显示空空如也
      },
      gettime() {
        return store.state.timelist
      },
    }
  }
</script>

<style scoped>
    li {
        width: 90%;
        margin-left: 10px;
        margin-top: 7px;
        border-width: 1.5px;
        border-color: darkgray;
        border-style: solid;
        border-radius: 6px;
        box-shadow: 1px 2px 2px 2px #ccc inset;
        padding-left: 10px;
        padding-top: 5px;
        padding-bottom: 5px;

    }

    h5 {
        text-align: center;
        padding-top: 15px;
    }

    .taozi {

        display: flex;
        justify-content: center;
        align-items: center;
    }

    .fanhui {
        margin-top: 27px;
        width: 387px;
        height: 37px;
        background: #42b983;
        border-radius: 5px;
        text-align: center;
        line-height: 2.1em;
        color: white;

    }

    .sss {
        margin-left: 170px;
        width: 50px;
        height: 25px;
        border-radius: 5px;
        background: #cccccc;
        color: white;
    }
</style>
