<template>
  <div class="hi">
    {{message}}
    <!-- v-on指令 -->
    <input type="button" @click="show_my_value('普通')" value="show_my_value1"/>    <!-- 调用方法 -->
    <input type="button" v-on:click="show_my_value('指令')" value="show_my_value2"/>    <!-- 指令调用方法 -->

    <!-- v-for指令 -->
    <ul>
      <li v-for="tech in technologies">
        {{tech}}
      </li>
    </ul>

    <!-- v-if指令 -->
    <div v-if="name === 'Java'">
      Java
    </div>
    <div v-else-if="name === 'PHP'">
      PHP
    </div>
    <div v-else-if="name === 'Python'">
      Python
    </div>

    <!-- v-for 优先级比 v-if 高 -->
    <ul>
      <li v-for="tech in technologies" v-if="tech.indexOf('n') === 0">
        {{tech}}
      </li>
    </ul>

    <!-- v-bind指令 -->
    <p v-bind:style="'color:'+color">v-blind</p>
    <input type="button" v-on:click="change_color()" value="修改颜色"/>

    <!-- v-model指令 -->
    <p>你好，{{model}}</p>
    <input type="text" v-model="model"/>


  </div>
</template>

<script>
export default {
  name: 'SayHi',
  data () {
    return {
      message:"你好 Vue！",    // 定义一个变量
      my_value:"默认值",
      technologies:[
        "nvm", "npm", "node", "webpack", "ecma_script"
      ],
      name:"Java",
      color:"green",
      model:"test"
    }
  },
  methods:{
    show_my_value:function(name){    // 定义一个方法
      alert("my_value: "+this.my_value)
      alert("name: "+name)
    },
    change_color:function(){
      this.color = "blue"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hi{
  color:red;
  font-size: 20px;
}
</style>
