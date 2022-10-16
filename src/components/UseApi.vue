<template>
  <div class="hello">
  <div>
  <button @click="GetListUser">Получить список пользователей</button>
  <div>{{json}}</div>
  <button @click="CreateUser">Создать пользоватля</button>
  <input type="text" v-model="name" placeholder="Имя">
  <input type="text" v-model="email" placeholder="email">
  <input type="password" v-model="password"  placeholder="Пароль">
  </div>
  </div>
</template>

<script>
export default {
  name: 'UseApi',
  data() {
  return {
  json: {},
  name: "",
  email: "",
  password: ""
  }
  },
  methods: {
  GetListUser: function() {
    fetch('http://192.168.25.81:81/api/user')
    .then(response => response.json())
    .then(response => this.json = response)
  },
  CreateUser: function() {
    let User = {
        name: this.name,
        email: this.email,
        password: this.pasword
    }
    fetch('http://192.168.25.81:81/api/user', {
        method: 'POST',
        mode: 'no-cors',
        headers: {
       'Content-Type': 'application/json;charset=utf-8'
          },
        body: JSON.stringify(User)
    })
  }
  }
}
</script>