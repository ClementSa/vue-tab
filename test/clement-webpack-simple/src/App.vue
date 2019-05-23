<template>
  <div id="app">
    <div class='tab'>
      <Tab :tab='tabNode'></Tab>
    </div>
    <div class='tab'>
      <Sildetab :silde='Sildetab'></Sildetab>
    </div>
  </div>
</template>

<script>
import Tab from './tab.vue'
import Sildetab from './sildetab.vue'

export default {
  data () {
    return {
      tabNode:{
        image:['./src/image/1.jpg','./src/image/2.jpg','./src/image/3.jpg','./src/image/4.jpg','./src/image/5.jpg'],
        index:0,
        bottomNode:-57,
        interval:null
      },
      Sildetab:{
        image:['./src/image/7.jpg','./src/image/2.jpg','./src/image/3.jpg','./src/image/4.jpg','./src/image/5.jpg','./src/image/6.jpg','./src/image/1.jpg']
      }
    }
  },
  components:{
    Tab,
    Sildetab
  }
}
</script>

<style>
*{margin:0;padding:0;list-style:none;}
body {
  font-family: Helvetica, sans-serif;
}
.active{background:#ccc}
.mydiv{width:200px;height:200px;background:blue}
</style>
