<template>
  <div id="templete">
    <form v-on:submit.prevent="checkForm">
      <label for="name">
        <p class="label-txt">ENTER YOUR NAME</p>
        <input id="name" v-model="user.name" type="text" class="input" @input="errors.name = null">
        <div class="line-box">
          <div class="line" />
        </div>
        <span v-if="errors.name">
          <br>
          <span class="errors">{{ errors.name }}</span>
        </span>
      </label>
      <label for="email">
        <p class="label-txt">ENTER YOUR EMAIL</p>
        <input id="email" v-model="user.email" type="text" class="input" @input="errors.email = null">
        <div class="line-box">
          <div class="line" />
        </div>
        <span v-if="errors.email">
          <br>
          <span class="errors">{{ errors.email }}</span>
        </span>
      </label>
      <label for="phone">
        <p class="label-txt">ENTER YOUR PHONE</p>
        <input id="phone" v-model="user.phone" type="text" class="input" @input="errors.phone = null">
        <div class="line-box">
          <div class="line" />
        </div>
        <span v-if="errors.phone">
          <br>
          <span class="errors">{{ errors.phone }}</span>
        </span>
      </label>
      <button type="submit">
        submit
      </button>
    </form>
    <div class="container">
      <div class="row">
        <div class="span5">
          <table class="table table-striped table-condensed">
            <thead>
              <tr>
                <th>Name</th>
                <th>Email</th>
                <th>Phone</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <!-- // eslint-disable-next-line vue/require-v-for-key -->
              <tr v-for="(item, index) in list" :key="index">
                <td>{{ item.name }}</td>
                <td>{{ item.email }}</td>
                <td>{{ item.phone }}</td>
                <td>
                  <button id="delete" v-on:click="deleteItem(index)">
                    Delete
                  </button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AddUser',
  data () {
    return {
      list: [],
      user: {
        name: null,
        email: null,
        phone: null
      },
      errors: {
        name: null,
        email: null,
        phone: null
      }
    }
  },
  methods: {
    checkForm () {
      console.log(this.user)
      if (this.user.name && this.user.email && this.user.phone) {
        this.save()
        return true
      }

      if (!this.user.name) {
        this.errors.name = 'Name is required.'
      }
      if (!this.user.email) {
        this.errors.email = 'Email is required.'
      }
      if (!this.user.phone) {
        this.errors.phone = 'Phone is required.'
      }
    },
    save () {
      this.list.push(this.user)
      this.user = {
        name: null,
        email: null,
        phone: null
      }
    },
    deleteItem (index) {
      this.list.splice(index, 1)
    }
  // layout: 'app'
  }
}
</script>

<style scoped>
@import "//maxcdn.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css";

span.errors {
  color: rgb(219, 43, 43);
  text-align: left;
}
form {
  width: 60%;
  margin: 60px auto;
  background: #efefef;
  text-align: center;
  padding: 60px 120px 80px 120px;
  -webkit-box-shadow: 2px 2px 3px rgba(0,0,0,0.1);
  box-shadow: 2px 2px 3px rgba(0,0,0,0.1);
}
label {
  display: block;
  position: relative;
  margin: 40px 0px;
}

.label-txt {
  position: absolute;
  top: -1.6em;
  padding: 10px;
  font-family: sans-serif;
  font-size: .8em;
  letter-spacing: 1px;
  color: rgb(120,120,120);
  transition: ease .3s;
}
.input {
  width: 100%;
  padding: 10px;
  background: transparent;
  border: none;
  outline: none;
}

.line-box {
  position: relative;
  width: 100%;
  height: 2px;
  background: #BCBCBC;
}

.line {
  position: absolute;
  width: 0%;
  height: 2px;
  top: 0px;
  left: 50%;
  transform: translateX(-50%);
  background: #8BC34A;
  transition: ease .6s;
}

.input:focus + .line-box .line {
  width: 100%;
}

.label-active {
  top: -3em;
}
button#delete:hover {
  background:rgb(233, 47, 47);
  color: #ffffff;
}
button {
  align-self: center;
  display: inline-block;
  padding: 12px 24px;
  background: rgb(220,220,220);
  font-weight: bold;
  color: rgb(120,120,120);
  border: none;
  outline: none;
  border-radius: 3px;
  cursor: pointer;
  transition: ease .3s;
}

button:hover {
  background: #8BC34A;
  color: #ffffff;
}
</style>
