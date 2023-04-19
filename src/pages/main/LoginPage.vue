<template>

  <div id="sm" class="row">

      <div  class="col-xs-12 col-md-6 text-center" id="login">
        <h5>華餅系統</h5>
        <!-- <img src="src/assets/休假2.png" style="width:300px;"> -->
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md" >
        <q-input
          outlined
          type="text"
          v-model="form.username"
          label="帳號"
          hint="請輸入帳號"
          lazy-rules
          :rules="[(val) => (val && val.length >= 4) || '最少4位數以上']"
        />
        <q-input
          outlined
          type="password"
          v-model="form.password"
          label="密碼"
          hint="請輸入密碼"
          lazy-rules
          :rules="[(val) => (val && val.length >= 4) || '最少4位數以上']"
        />
        <div>
          <q-btn
            label="清除"
            type="reset"
            color="primary"
            flat
            class="q-ml-sm"
          />
          <q-btn label="送出" color="primary" @click="login" />

        </div>
      </q-form>
      <q-btn
      outline
        class="register1"
        label="未註冊帳號"
        type="button"
        color="primary"
        to="/register"
      />
    </div>

  </div>
</template>

<script setup>
// import { useQuasar } from 'quasar'
import { reactive } from 'vue'
// import { useUserStore } from 'src/stores/user'
// import { useRouter } from 'vue-router'
import { api } from 'src/boot/axios'

// const router = useRouter()
// const $q = useQuasar()
// const user = useUserStore()
const form = reactive({
  username: '',
  password: ''
})

// function login () {
//   router.push('/admin')
// }
// // if (user.role === 1 || user.isAdmin === true) {
//   router.push('/admin')
// } else if (user.isLogin === true && user.role === 0) {
//   router.push('/user')
// } else {
//   router.push('/login')
// }

// const accept = ref(false)
const login = async () => {
  const result = await api.post('/login', form)
  console.log(result)
}
// const logout = async () => {
//   await user.logout()
// }
// const onSubmit = async () => {
//   if (form.account && form.password !== null) {
//     await login()
//     if (user.role === 1 || user.isAdmin === true) {
//       router.push('/admin')
//     } else if (user.isLogin === true && user.role === 0) {
//       router.push('/user')
//     } else {
//       router.push('/login')
//     }
//   } else {
//     $q.notify({
//       color: 'red-5',
//       textColor: 'white',
//       icon: 'warning',
//       message: '輸入錯誤'
//     })
//   }
// }

// function onReset () {
//   form.name = ''
//   form.account = ''
//   form.password = ''
//   form.phone = ''
//   accept.value = false
// }
</script>

<style lang="scss" scoped>
.register1{
margin-top: 20px;
margin-left: 30px;
}
#sm {
  width: 100%;
  margin-top: 50px;
.col-md-6{
margin: auto;
padding: 12px;
margin-top: 20%;
}
}
#login{
background: #eeeeee;
padding: 20px;
border: 5px solid #eeeeee;
border-radius: 5%;
width: 40%;
}
@media screen and (min-width: 768px) {
  #login{
background: #eeeeee;
padding: 20px;
border: 5px solid #eeeeee;
border-radius: 5%;
width: 40%;

}
}

</style>
