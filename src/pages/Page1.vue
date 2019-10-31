<template>
  <div id="page">
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
  </div>
</template>
<script>
export default {
  name: "Page",
  data() {
    return {
      message: "hello1",
      seen: true,
      todos: [
        { text: "学习 JavaScript" },
        { text: "学习 Vue" },
        { text: "整个牛项目" }
      ],
      msg: "hahaha",
      foo: "baa"
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
    rm: function() {
      this.msg = this.msg
        .split("")
        .reverse()
        .join("");
    },
    reversedMessage1: function () {
    return this.msg.split('').reverse().join('')
  }
  }
};
</script>