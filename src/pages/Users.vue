<template>
  <div class="wrapper-content wrapper-content--fixed">

    <section>
      <div class="container">

        <!--        table-->
        <table>

          <!--          head-->
          <thead>
          <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Gender</th>
          </tr>
          </thead>

          <!--          body-->
          <tbody>
          <tr v-for="user in users" :key="user.id">
            <td>
              <img :src="user.img" :alt="user.name">
              <span>{{ user.name }}</span>
            </td>
            <td>{{ user.age }}</td>
            <td>{{ user.gender }}</td>
          </tr>
          </tbody>

        </table>

      </div>

    </section>

  </div>
</template>

<script>

import axios from 'axios'

export default {
  name: "Users",
  data() {
    return {
      users: []
    }
  },
  created() {
    axios
        .get('http://localhost:3000/users')
        .then(response => {
          // console.log(response.data)
          this.users = response.data
        })
        .catch(error => {
          console.log(error)
        })


    // this.users = [
    //   {
    //     id: 1,
    //     name: 'Jack',
    //     age: 22,
    //     gender: 'male'
    //   },
    //   {
    //     id: 2,
    //     name: 'Alex',
    //     age: 24,
    //     gender: 'male'
    //   }
    // ]
  }
}
</script>

<style lang="scss" scoped>
img {
  width: 60px;
  height: auto;
  border-radius: 50%;
  margin-right: 16px;
}
</style>