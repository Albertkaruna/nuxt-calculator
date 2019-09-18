<template>
  <v-app dark class='mt-12'>
    <v-card max-width="400" class="mx-auto">
      <v-card-actions>
        <v-container>
          <v-layout column wrap>
           <v-alert outlined color="cyan darken-2" class="text-right"><strong>{{expression}}</strong></v-alert>
          </v-layout>
          <!-- <v-layout row wrap v-for="i in 6" :key="i" class="ma-1">
            <v-btn v-for="j in 4" :key="j" class="ma-1" large v-on:click="addExpression">{{ btn_vlaues[i-1][j-1]}}</v-btn>
          </v-layout> -->
          <v-layout row wrap class=" cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="addExpression"> % </v-btn>
            <v-btn class="ma-1" large v-on:click="sqrt"> √ </v-btn>
            <v-btn class="ma-1" large v-on:click="clearExpression"> CE </v-btn>
            <v-btn class="ma-1" large v-on:click="backspace"> <v-icon> mdi-backspace </v-icon> </v-btn>
          </v-layout>
          <v-layout row wrap class="cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="square"> <sub>x</sub> <sup>2</sup> </v-btn>
            <v-btn class="ma-1" large v-on:click="divideByOne"> 1/<sub>x</sub> </v-btn>
            <v-btn class="ma-1" large v-on:click="inverseSign"> ± </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> / </v-btn>
          </v-layout>
          <v-layout row wrap class="cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="addExpression"> 7 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 8 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 9 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> * </v-btn>
          </v-layout>
          <v-layout row wrap class="cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="addExpression"> 4 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 5 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 6 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> - </v-btn>
          </v-layout>
          <v-layout row wrap class="cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="addExpression"> 1 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 2 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 3 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> + </v-btn>
          </v-layout>
          <v-layout row wrap class="cyan darken-2 ma-1">
            <v-btn class="ma-1" large v-on:click="addExpression"> 0 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> 00 </v-btn>
            <v-btn class="ma-1" large v-on:click="addExpression"> . </v-btn>
            <v-btn class="ma-1" large v-on:click="equal"> = </v-btn>
          </v-layout>
        </v-container>
      </v-card-actions>
    </v-card>
  </v-app>
</template>

<script>
import {evaluate} from 'mathjs'

export default {
  data() {
    return {
      expression : '0',
    };
  },
  methods:{
    addExpression(event){
      if(this.expression==='0')
        this.expression=this.expression.slice(0,-1)
      let exp=(event.originalTarget.innerText).trim();
      this.expression=this.expression.concat(exp);
    },
    equal(){
      if(this.expression.trim()==='') return
      this.expression=evaluate(this.expression).toString();
    },
    clearExpression(){
      this.expression='0'
    },
    sqrt(){
      this.expression=Math.sqrt(this.expression).toString()
    },
    square(){
      this.expression = (this.expression*2).toString()
    },
    divideByOne(){
      if(this.expression==='0') return;
      this.expression=(1/this.expression).toString()
    },
    backspace(){
      this.expression=this.expression.slice(0,-1).toString()
      if(this.expression.length===0)
        this.expression='0'
    },
    inverseSign(){
      this.expression = (parseInt(this.expression)*(-1)).toString()
    }
  },
};
</script>

<style>
</style>