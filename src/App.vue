<template>
  <div id="app" class="container">
    <div class="text-center" v-if="mainVal == secondVal && secondVal == thirdVal">
      <h1>Congratulations!</h1>
    </div>
    <div class="text-center" v-if="mainVal != secondVal || secondVal != thirdVal">
      <h2>Make Counters Equal!</h2>
      <p>Main -> I/D -> 1,2,3</p>
      <p>Second -> I/D -> 1,2</p>
      <p>Third -> I/D -> 2,3</p>
    </div>

    <form class="form">
      <label>Counter Main :</label>
      <div class="d-flex">
        <input type="text" placeholder="Main Counter" ref="inputRef" :value="mainVal" disabled>
        <button type="button" class="btn btn-primary ms-5" @click="Calculate1(1)">
          <i class="fas fa-plus"></i>
        </button>
        <button type="button" class="btn btn-danger ms-2" @click="Calculate1(-1)">
          <i class="fas fa-minus"></i>
        </button>
        <input type="text" placeholder="Name" class="right">
      </div>
    </form>
    <!-- <CounterTwo @secondVal="Sum({value:$event.target.value})"/> -->
    <CounterTwo @onClick="Calculate2" :value="secondVal" />
    <CounterThree @onClick="Calculate3" :value="thirdVal"/>
  </div>
</template>

<script>
import CounterThree from './components/CounterThree.vue';
import CounterTwo from './components/CounterTwo.vue';

export default {
  name: 'App',
  components: {
    CounterTwo,
    CounterThree,
  },
    data(){
    return {
      mainVal: Math.floor(Math.random() * (10 - 1 + 1)) + 1,
      secondVal: Math.floor(Math.random() * (10 - 1 + 1)) + 1,
      thirdVal: Math.floor(Math.random() * (10 - 1 + 1)) + 1,
      // mainVal: 1,
      // secondVal: 1,
      // thirdVal: 1,
    }
  },
  // created(){
  //   this.initialVal = 0
  // },
  methods:{
    // Sum({value}){
    //   console.log(value);
    //   // this.$refs.inputRef.$el.value =
    // }
    Calculate1(val){
      // console.log(val);
      this.mainVal += val;
      this.secondVal += val;
      this.thirdVal += val;
    },
    Calculate2(val){
      // console.log('print');
      this.mainVal += val;
      this.secondVal += val;
    },
    Calculate3(val){
      // console.log('print');
      this.secondVal += val;
      this.thirdVal += val;
    }
    // Sum(e){
    //   e.preventDefault();
    //   value = e.target.value;
    //   console.log(value);
    // }
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
  margin-top: 60px;
}
* {
  box-sizing: border-box;
}

form {
  padding: 1em;
  /* background: #f9f9f9; */
  /* border: 1px solid #c1c1c1; */
  margin-top: 2rem;
  /* max-width: 600px; */
  /* margin-left: auto; */
  /* margin-right: auto; */
  padding: 1em;
  /* margin-left : 0px !important; */
  border-bottom: 2px dashed black;
}
form input {
  width: 20%;
  margin-bottom: 1rem;
  background: #fff;
  border: 1px solid #9c9c9c;
}

label {
  text-align: right;
  display: block;
  padding: 0.5em 1.5em 0.5em 0;
}

input {
  width: 100%;
  padding: 0.7em;
  margin-bottom: 0.5rem;
}
input:focus {
  outline: 3px solid green;
}

.right{
    /* display: flex; */
    /* justify-content: flex-end; */
    float: right;
    margin-left: auto;
    /* margin-left: 200px; */
}
.btn{
  width: 50px;
  height: 40px;
}

@media (min-width: 400px) {
  form {
    overflow: hidden;
  }

  label {
    float: left;
    width: 200px;
  }

  input {
    float: left;
    width: calc(100% - 200px);
  }

  

}
</style>
