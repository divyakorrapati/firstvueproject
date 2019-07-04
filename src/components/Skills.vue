<template>
  <div class="container">
    <div class="holder">

      <form @submit.prevent="addSkill">
      <input type="text" placeholder="Enter a skill you have.." v-model="skill" v-validate="'min:5'" name="skill">
      
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
      </transition>

    </form>


      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutDown">
          <li v-for="(data, index) in skills" :key='index'>
            {{data.skill}}
            <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
            </li>
        </transition-group>
      </ul>

      <p>These are the skills that you possess.</p>

    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [
          
      ]
    }
  },
      methods : {
      addSkill() {
        this.$validator.validateAll().then((result) => {
          if (result) {
            this.skills.push({skill: this.skill});
            this.skill = '';
          } else {
            console.log('Not valid');
          }
        })
      },
      remove(id) {
        this.skills.splice(id, 1);
      }
      }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 

  .holder {
    background: rgb(2, 93, 129);
  }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }
  
  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: rgb(120, 196, 236);
    border-left: 5px solid rgb(246, 114, 62);
    margin-bottom: 2px;
    color: rgb(31, 83, 83);
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: rgb(68, 37, 37);
  }

  .container {
    box-shadow: 0px 0px 40px rgb(105, 78, 78);
  }

input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #27dfdf;
    color: #687F7F;
  }

  .alert {
    background: #e2af07;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
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
  }
  50% {
    transform: scale(1.5);
  }
  100% {
    transform: scale(1);
  }
}

i{
  float:right;
  cursor: pointer;
}
</style>