<template>
    <div class="zong">
        <form action="" v-if="!isReg" class="fff">
            <h3>欢迎登陆</h3>
            <div class="se">用户名</div>
            <input type="text" v-model="name" class="namee"><br/><br/><br/>
            <div class="se">密码</div>
            <input type="password" v-model="password" class="passwood"><br/><br/><br/>
            <button type="button" @click="login()" class="anniu1" @mouseover="mouses($event)" @mouseout="outt">登录
            </button>
            &nbsp&nbsp&nbsp
            <button type="button" @click="reg()" class="anniu2" @mouseover="mouses($event)" @mouseout="outt2">注册
            </button>
        </form>
        <form action="" v-else>
            <h3>请输入以下信息</h3>
            <div class="sbb">用户名</div>
            <input type="text" v-model="name" class="nameee"><br/><br/>
            <div class="sb">密码</div>
            <input type="password" v-model="password" class="pass"><br/><br/>
            <div class="sg">再次密码</div>
            <input type="password" v-model="repeat" class="repeatpass"><br/><br/><br/>
            <button type="button" @click="addUser()" class="anniu1" @mouseover="mouses($event)" @mouseout="outt">确定
            </button>
            &nbsp&nbsp&nbsp&nbsp
            <button type="button" @click="cancel()" class="anniu2" @mouseover="mouses($event)" @mouseout="outt2">返回
            </button>
        </form>
    </div>
</template>
<script>

  export default {

    name: "Login",
    data() {
      return {
        isReg: false,
        name: '',
        password: '',
        repeat: '',
        isgaibian: false,
      }
    },

    methods: {
      login() {
        if (localStorage.getItem("name") === this.name && localStorage.getItem("password") === this.password) {
          this.$store.commit('setName', this.name)
          this.name = ''
          this.password = ''
          this.$router.push('/home/user') /*直接转入user路径*/
        } else {
          alert('用户名或密码输入不正确')
        }

      },
      mouses($event) {
        $event.currentTarget.className = "aa active"
      },
      outt($event) {
        $event.currentTarget.className = "anniu1"
      },
      outt2($event) {
        $event.currentTarget.className = "anniu2"
      },
      reg() {
        this.isReg = true
      },
      cancel() {
        this.isReg = false
      },
      addUser() {
        if (this.password === this.repeat && this.password !== '' && this.name !== '') {
          localStorage.setItem("name", this.name),
            localStorage.setItem("password", this.password)
          this.name = ''
          this.password = ''
          this.isReg = false
          alert('注册成功！')
        } else {
          alert('两次密码输入的不一致或者用户名和密码为空！！！')
        }
      }
    }
  }
</script>

<style scoped lang="scss">
    $a: red;
    .aa {
        width: 150px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #ccc;
        color: #ffffff;
        font-weight: bold;
        box-shadow: 1px 2px 2px 2px darkgray inset;
    }

    .zong {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .fff {
        padding-top: 30px;
    }

    .se {
        float: left;
        padding-left: 20px;
    }

    h3 {
        padding-left: 30px;
        padding-top: 20px;
        padding-bottom: 25px;
        color: $a;
    }

    .namee {
        width: 235px;
        height: 25px;
        border-radius: 5px;
        margin-left: 3px;
    }

    .passwood {
        margin-left: 19px;
        width: 235px;
        height: 25px;
        border-radius: 5px;
    }

    .anniu1 {
        width: 150px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #42b983;
        color: #ffffff;
        font-weight: bold;
    }

    .anniu2 {
        width: 150px;
        height: 35px;
        margin-left: 20px;
        border-radius: 15px;
        background: #ffffff;
        color: #42b983;
        font-weight: bold;
    }

    .pass {
        margin-left: 19px;
        width: 235px;
        height: 25px;
        border-radius: 5px;
    }

    .repeatpass {
        width: 235px;
        height: 25px;
        border-radius: 5px;
        margin-left: 20px;
    }

    .sb {
        float: left;
        padding-left: 58px;
    }

    .sg {
        float: left;
        padding-left: 25px;
    }

    .sbb {
        float: left;
        padding-left: 43px;
    }

    .nameee {
        width: 235px;
        height: 25px;
        border-radius: 5px;
        margin-left: 17px;
    }
</style>
