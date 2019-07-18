<template>
  <div class="hello">
    <div class="holder">
      <form @submit.prevent="addLeson">
        <input class="hitam" type="text" placeholder="Enter a new lesson.. " v-model="home" v-validate="'min:5'" name="home">
        
        <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('home')">{{ errors.first('home') }}</p>
        </transition>

        <input type="checkbox" id="checkbox" v-model="checked">
      </form>
      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in homes" :key="index">
            {{ index }}.{{ data.home}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>
        </transition-group>
      </ul> 
      <!-- <ul> 
      <li v-if="homes.length >= 1"> You have more then 1 skill </li>
       <li v-else>You have less then or equal to 1 skill</li>
      </ul>
      <ul>
        <li v-for="(data, index) in homes" :key="index">{{ data.home}}</li>
      </ul> -->
      
      <p> These are the skills that you possess.</p>
      <div v-bind:class="alertObject"></div>
    </div>
  </div>
</template>
<script>
export default { 
  name: 'homes',
  data() {
    return {
      checked: false,
      home: '',
      homes: [
        {home: 'vue.Js'},
        {home: 'Frontend Developer'}
      ],
      showAlert: true,
      alertObject: {
        aleert: true
      }
    }
  },
  methods: {
    addLeson(){
      this.$validator.validateAll().then((result) =>{
        if (result) {
            this.homes.push({home: this.home})
            this.home = '';
            console.log('this checkbox value is : ' + this.checked);
        }else{
          console.log('Not Valid');
        }
      })
    },
    remove(id){
      this.homes.splice(id,1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";
  .alert{
    background-color:darkgrey;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }
  .aleert{
    background-color: black;
    width: 100%;
    height: 30px;
  }

   .holder {
    background: #fff;
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  .alert-in-enter-active {
    animation: bounce-in .5s;
  }
  
  .alert-in-leave-active {
    animation: bounce-in .5s reverse;
  }

  @keyframes bounce-in {
    0% {
      transform: scale(0);
    } 50% {
      transform: scale(1.5);
    } 100% {
      transform: scale(1);
    }
  }
  i {
    float: right;
    cursor: pointer;
  }

  .hitam {
    background-color: #3E5252;
    color: white;
    width: 400px;
    height: 30px;
  }
</style>
