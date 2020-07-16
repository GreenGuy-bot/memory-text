<template>
    <div>
        <div class="www"><img :src='imgUrl' class="vuetupian"></div>
        <P class="ssswww">{{$store.state.namee}}</P>
<!--        用之前注册的$store直接获取Name-->
        <p class="huanyin">欢迎来到个人中心</p>
        <div class="wwoo">
            <div @click="quadd" class="tianjia">添加</div>
        </div>
    </div>
</template>

<script>

  export default {
    name: "User",
    data() {
      return {
        imgUrl: require('../assets/logo.png')
      }
    },
    methods: {
      quadd() {
        this.$router.push('/add')
      }
    },
    computed: {

    }
  }
</script>

<style scoped>
    .wwoo {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .www {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .vuetupian {
        padding-top: 50px;
    }

    .ssswww {
        font-size: 17px;
        text-align: center;
    }

    .huanyin {
        text-align: center;
        font-size: 17px;
        padding-top: 5px;
    }

    .tianjia {
        margin-top: 27px;
        width: 387px;
        height: 37px;
        background: #42b983;
        border-radius: 5px;
        text-align: center;
        line-height: 2.1em;
        color: white;
    }
</style>
