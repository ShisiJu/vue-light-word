# vue-light-word

基于vue, 通过设置 vue指令来高亮文本

下面是如何使用

## 加入全局指令

```js
import Vue from 'vue'
import VueHighLight from 'vue-light-word'

Vue.config.productionTip = false
// 在new之前注册v-light
// VueHighLight(Vue, {defaultClass: 'default-light'})
VueHighLight(Vue)
new Vue({
  render: h => h(App),
  store
}).$mount('#app')
```

## 使用

注意: 需要自己写一个全局的高亮class `.default-light`, 处理默认样式问题

```css
 .default-light {
    color: red;
  }
```

```html
<template>
  <div id="d1">
    <span v-light="[context, light]"></span>
    <input type="text" v-model="context">
  </div>
</template>
<script>


export default {
  name: 'App',
  data () {
    return {
      context: '你好, hello world<script><\/script> ',
      light: 'world'
    }
  },
}
</script>

<style>
  .default-light {
    color: red;
  }
</style>
```

其中 v-light="[context, light, customClass]"

1. context 是整个文本
2. light 是想要高亮的文本
3. 自定义的样式, 如果不传则使用默认的class


