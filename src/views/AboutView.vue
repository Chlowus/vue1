<template lang="">
  <div>
    <button class="btn2" @click="decrement()">Decrement</button>
    <h1>Counter -> <span>{{counter}}</span></h1>
    <button @click="increment()">Increment</button>
  </div>
  <img :src="imgUrl">
  <div>
    <h4 :class="{hello:check}">Conditional rendering</h4>
    <h1 v-if="check">The value is true</h1>
    <h1 v-else>The value is false</h1>
    <button @click="change()">Change state</button>
    <h1 v-show="check">This contains the v-show</h1>
    <ul>
      <!-- <li v-for="(sport, index) in sports" :key="index">{{sport}}</li> -->
      <li v-for="({message},index) in objects" :key="index">{{message}}</li>
    </ul>
    <!-- ONE WAY BINDING -->
    <h3>{{oneWayText}}</h3>
    <!-- TWO WAT BINDING -->
    <h3>{{twoWayText}}</h3>
    <input type="text" v-model="twoWayText">
  </div>
  <!-- <info-comp first-name="hehe" last-name="hehehehehe"/>
  <info-comp first-name="hehe1"/>
  <info-comp :object-data='singleObject'/> -->
  <info-comp>
    Hehe I am using slots
  </info-comp>
  <slot-comp>
    <template #slotTitle>
      Card Slot
    </template>
    <template #default>
      <img :src="imgUrl">
    </template>
  </slot-comp>
</template>

<script>
/* eslint-disable*/
import InfoComp from '../components/infoComp.vue'
import SlotComp from '../components/slotComp.vue'

export default {
  data(){
    return {
      counter:0,
      imgUrl:'https://www.hollywoodreporter.com/wp-content/uploads/2019/11/the_end_of_the_fing_world_still.jpg?w=1296',
      check:true,
      sports:['soccer','netball','volleyball'],
      objects:[
        {message:'Hello There 1', id:1},
        {message:'Hello There 2', id:2},
        {message:'Hello There 3', id:3},
      ],
      singleObject: {
        name:'Chloe',
        surname:'Smith'
      },
      oneWayText:'hehe',
      twoWayText:'hehe2.0',
    }
  },
  components:{
    InfoComp,
    SlotComp
  },
  methods: {
    increment(){
      this.counter++
    },
    decrement(){
      this.counter--
    },
    change(){
      this.check = !this.check
    }
  }
}
</script>
<style scoped>
  h1{
    color:blue
}
img{
  width:200px;
  height:200px;
  object-fit: cover;
}
</style>