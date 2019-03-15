<template>
  <div class="dashboard-container">
    <transition name="button"><el-button class="login-button" v-if="show" @click.native.prevent="handleOpenLogoutDialog">M</el-button></transition>
    <transition name="card">
      <el-card class="logout-card" v-if="!show">
        <el-button type="primary" style="width:100%;" @click.native.prevent="handleLogout">
          Sign out
        </el-button>
      </el-card>
    </transition>
    <div class="dashboard-text">name:{{ name }}</div>
    <el-button type="primary" style="width:100%;" @click.native.prevent="handleGoForMore">go for more</el-button>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import { logout } from '@/api/login'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name',
      'roles'
    ])
  },
  data(){
    return {
      show: true
    }
  },
  methods:{
    handleOpenLogoutDialog() {

      this.show = !this.show
    },
    handleLogout() {
      this.show = !this.show
      this.$store.dispatch('LogOut').then(() => {
        location.reload()
      })
    },
    handleGoForMore() {
      this.$router.push('/goformore')
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
@keyframes show-login-card {
  0% {
      top: 10%;
      left: 90%;
      -moz-transform: translate(-10%, -90%);
      transform: translate(-10%, -90%);
      -o-transform: translate(-10%, -90%);
      transform: translate(-10%, -90%);
      border-radius: 400px;
      width: 40px;
      height: 40px;
    }
  // 25% {top: 30%; left: 80%; -ms-transform: translate(-30%, -80%); transform: translate(-30%, -80%); border-radius: 300px; width: 100px; height: 320px;}
  // 50% {top: 50%; left: 70%; -ms-transform: translate(-50%, -70%); transform: translate(-50%, -70%); border-radius: 150px; width: 200px; height: 560px;}
  // 75% {top: 60%; left: 60%; -ms-transform: translate(-60%, -60%); transform: translate(-60%, -60%); border-radius: 80px; width: 300px; height: 690px;}
  100% {
      top: 50%;
      left: 50%;
      -moz-transform: translate(-50%, -50%);
      transform: translate(-50%, -50%);
      -o-transform: translate(-10%, -90%);
      transform: translate(-50%, -50%);
      border-radius: 20px;
      width: 600px;
      height: 200px;
    }
}

.login-button {
  top: 10%;
  left: 90%;
  border-radius: 400px;
  width: 40px;
  height: 40px;
  transform: translate(-10%, -90%);
  -moz-transform: translate(-10%, -90%);
  -o-transform: translate(-10%, -90%);
  transform: translate(-10%, -90%);
  margin: 0;
  position: absolute;
}

.logout-card {
  top: 50%;
  left: 50%;
  border-radius: 20px;
  width: 600px;
  height: 200px;
  transform: translate(-50%, -50%);
  -moz-transform: translate(-50%, -50%);
  -o--transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  margin: 0;
  position: absolute;
}

.button-enter-active {
  animation-name: show-login-card;
  animation-timing-function: ease-in-out;
  animation-duration: 0.48s;
  animation-fill-mode: forwards;
  animation-direction: reverse;
}

.button-leave-active {
  animation-name: show-login-card;
  animation-timing-function: ease-in-out;
  animation-duration: 0.48s;
  animation-fill-mode: forwards;
}

.card-enter-active {
  animation-name: show-login-card;
  animation-timing-function: ease-in-out;
  animation-duration: 0.48s;
  animation-fill-mode: forwards;
}

.card-leave-active {
  animation-name: show-login-card;
  animation-timing-function: ease-in-out;
  animation-duration: 0.48s;
  animation-fill-mode: forwards;
  animation-direction: reverse;
}

$bg:#eeeeeed8;
$dark_gray:#889aa4;
$light_gray:#303030;
  .login-button {
    top: 10%;
    left: 90%;
    border-radius: 400px;
    width: 40px;
    height: 40px;
    transform: translate(-10%, -90%);
    -moz-transform: translate(-10%, -90%);
    -o-transform: translate(-10%, -90%);
    transform: translate(-10%, -90%);
    margin: 0;
    position: absolute;
  }

.dashboard {
  &-container {
    position: relative;
    height: 100%;
    width: 100%;
    background-color: $bg;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
