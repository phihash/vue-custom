<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link> |
      <router-link to="/fire">Fire</router-link>
    </div>
    <router-view/>
    <hr>
   <div>
     <h3>ボタンカスタマイザ</h3>
     <button :style="styleObject">{{customButtonName}}</button>
     <h4>ボタンテキスト</h4>
     <input type="text" v-model="customButtonName">
     <h4>フォントサイズ</h4>
     <input type="range" v-model="fontSize"> {{fontSize}}
     <h4>カラー</h4>
     <input type="color" v-model="colorCode"> {{colorCode}}
     <h4>バックグラウンドカラー</h4>
     <input type="color" v-model="bgColorCode"> {{bgColorCode}}
     <h4>パディング</h4>
     <input type="range" v-model="padding"> {{padding}}
     <h4>ボーダーラジアス</h4>
     <input type="range" v-model="radius"> {{radius}}
   </div>
    <hr>
    <h3>基本的なこと</h3>
    <p>{{test}}</p>
    <button @click="plus()">カウンター</button>
    <button v-on:click="minus()">マイナス</button>
    <p>{{counter}}</p>
  </div>
</template>

<script>
export default {
  data () {
    return {
      test: 'Test',
      counter:0,
      customButtonName:"カスタムボタン",
      fontSize:22,
      colorCode:"#f8ede8",
      bgColorCode:"#e18f41",
      padding:20,
      radius:4,
    }
  },
  methods: {
    plus:function(){
      this.counter++;
    },
    minus:function(){
      if(this.counter == 0) return;
      this.counter--;
    },
  },
  computed:{
    styleObject:function(){
      return {
        fontSize:this.fontSize + "px",
        padding:this.padding+ "px",
        borderRadius:this.radius+ "px",
        color:this.colorCode,
        backgroundColor:this.bgColorCode,
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
