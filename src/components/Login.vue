<template>
  <div class="Login">
    <!--<form @submit.prevent="submit">-->
      <form method="post" action="http://127.0.0.1:8000/Login/">
      <p>登录</p>
      <div>
        <label for="username">用户名:</label>
        <input id="username" v-model="login.username" name="username"/>
      </div>
      <div>
        <label for="password">密&nbsp;&nbsp;码:&nbsp; </label>
        <input id="password" type="password" v-model="login.password"/>
      </div>
      <button type="submit" v-on:click="checkuser">提交</button>
    </form>
    <!--<p>{{username}}</p>-->
    <!--<p>{{password}}</p>-->
    <p>{{err_msg}}</p>
  </div>
</template>

<script>
  export default {
    name: "Login",
    data() {
      return {
        username: '',
        password: '',
        err_msg: '',
        login: {}
      }

    },
    methods: {
      checkuser: function () {
        if (this.login.username.length == 0) {
          this.err_msg = '用户名不能为空';
        }
        else {
          this.err_msg = '';
        }
      },
      submit: function () {
        var formdata = JSON.stringify(this.login);
        var url = 'http://localhost:8000/Login/';
        // var url = 'http://127.0.0.1:8000/Login/';
        // this.$http.post(url,formdata).then(function (response) {
        //   alert(response)
        // }).catch(function (error) {
        //   console.log(error)
        // })
        this.$http.post(
          url, formdata, {
            emulateJSON: true
          }, {
            'headers': {
              'Content-Type': 'application/json'
            }
          }
        ).then(function (res) {
        }, function (res) {
        })
        // this.$http.jsonp(url, formdata,
        //   {
        //     headers: {},
        //     emulateJSON: true
        //   }).then((response) => {
        //   // this.movie = response.data;
        //   // console.log(this.movie);
        //   alert(response)
        // });
      },
      computed: {}
    }
  }
</script>

<style scoped>

</style>
