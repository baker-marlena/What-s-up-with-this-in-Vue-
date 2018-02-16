<template>
  <div class="hello">
    <h1>What is Up with 'this'?</h1>
    <p>
      {{msgPrint}}
    </p>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Point at me!',
      msgPrint: ''
    };
  },
  mounted() {
    // console.log('mounted', this);
    // console.log('message', this.msg);
    // this.fatArrow();
    // this.keyword();
    // this.methodDef();
    // this.callbackFunction();
    // this.callbackArrow();
    // this.timeout();
    this.timeoutArrow();
  },
  methods: {
    methodDef() {
      console.log('no arrow', this);
      this.msgPrint = this.msg;
    },
    fatArrow: () => {
      console.log('fat arrow', this);
      this.msgPrint = this.msg;
    },
    keyword: function()  {
      console.log('keyword', this);
      this.msgPrint = this.msg;
    },
    timeout() {
      setTimeout(function(){
        console.log('timeout', this);
        this.msgPrint = this.msg;
      }, 100)
      clearInterval();
    },
    timeoutArrow() {
      setTimeout(() => {
        console.log('timeout arrow', this);
        this.msgPrint = this.msg;
      }, 100)
      clearInterval();
    },
    callbackFunction() {
      const arr = ['a'];
      arr.forEach(function(val) {
        console.log('callback function', this);
        this.msgPrint = this.msg;
      })
    },
    callbackArrow() {
      const arr = ['a'];
      arr.forEach((val) => {
        console.log('callback arrow', this);
        this.msgPrint = this.msg;
      })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.hidden {
  display: none;
}
</style>
