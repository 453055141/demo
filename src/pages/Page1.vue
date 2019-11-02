<template>
  <div id="page" :class="[activeClass, errorClass]">
    <span :title="message">鼠标悬停几秒钟查看此处动态绑定的提示信息！</span>
    <p v-if="seen">hehe</p>
    <ol>
      <li v-for="(item, index) in todos" :key="index">{{item.text}}</li>
    </ol>
    <p>{{msg}}</p>
    <button v-on:click="rm">反转</button>
    <input v-model="msg" />
    <p>{{foo}}</p>
    <p v-once>这个不会改变：{{foo}}</p>
    <button @click="foo='baz'">change it</button>
    <button v-bind:disabled="true">Button</button>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <p>Computed reversed message: "{{ reversedMessage1() }}"</p>
    <h1 v-if="awesome">vue is awesome</h1>
    <h1 v-else>Oh no</h1>
    <div v-if="Math.random()>0.5">now you see me</div>
    <div v-else>now you don't</div>
    <div v-if="loginType === 'username'">
      <label>Username</label>
      <input placeholder="Enter your username" key="username" />
    </div>
    <div v-else>
      <label>Email</label>
      <input placeholder="Enter your email address" key="email" />
    </div>
    <button @click="changeLoginType">change login type</button>
    <ul>
      <!-- <li v-for="(item, index) of items" :key="index">
            {{index}}-{{item.message}}
      </li>-->
      <li v-for="(value, name,index) in object" :key="index">{{ name }}: {{ value }}</li>
    </ul>
    <div>
      <button @click="counter += 1">add 1</button>
      <p>The button above has been clicked {{ counter }} times.</p>
      <button @click="greet">Greet</button>
      <button v-on:click="warn('Form cannot be submitted yet.', $event)">Submit</button>
    </div>
  </div>
</template>

  </div>
</template>
<script>
export default {
  name: "Page",
  data() {
    return {
      counter: 0,
      message: "hello1",
      seen: true,
      object: {
        title: "How to do lists in Vue",
        author: "Jane Doe",
        publishedAt: "2016-04-10"
      },
      todos: [
        { text: "学习 JavaScript" },
        { text: "学习 Vue" },
        { text: "整个牛项目" }
      ],
      items: [
        { message: "学习 JavaScript" },
        { message: "学习 Vue" },
        { message: "学习 Html" },
        { message: "整个牛项目" }
      ],
      msg: "hahaha",
      foo: "baa",
      activeClass: "active",
      errorClass: "text-danger",
      awesome: true,
      loginType: "Email"
    };
  },
  computed: {
    reversedMessage: function() {
      return this.msg
        .split("")
        .reverse()
        .join("");
    }
  },
  methods: {
      warn: function (message, event) {
    // 现在我们可以访问原生事件对象
    if (event) event.preventDefault()
    alert(message)
  },
    greet: function(event) {
      alert("Hello ");
      if (event) {
        alert(event.target.tagName);
      }
    },
    rm: function() {
      this.msg = this.msg
        .split("")
        .reverse()
        .join("");
    },
    reversedMessage1: function() {
      return this.msg
        .split("")
        .reverse()
        .join("");
    },
    changeLoginType: function() {
      if (this.loginType === "username") {
        this.loginType = "email";
      } else {
        this.loginType = "username";
      }
    }
  }
};
</script>