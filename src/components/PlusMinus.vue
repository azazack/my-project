<template lang="pug">
  .button
    button(v-on:click="minuss()" class="btn" :disabled="disabled") -
    input.inpt(type="number" v-model="newvalue" onkeypress="return event.charCode >=48" max=20 :disabled="disabled" )
    button(v-on:click="pluss()" class="btn" :disabled="disabled" ) +
</template>

<script lang="ts">
 import {Vue,Component,Prop} from "vue-property-decorator";
@Component({})
 export default class Pluss extends Vue{
    @Prop({default: '1'}) min: number;
    @Prop({default: '20'}) max: number;
    @Prop() disabled?:boolean;

    newvalue: number = 1;
    minuss() {
        if ((this.newvalue) > this.min) {
            this.newvalue--;
        }
    }
    pluss() {
        if ((this.newvalue) < this.max) {
            this.newvalue++;
        }
    }

}


</script>

<style lang="scss">
  @import "../stylesheets/variable";
  @import "~bootstrap/scss/buttons";

  .button {
    display: inline-block;
    .btn {
      background-color: #c7c7c7;
      color: #2aa3ff;
      margin-top: -3px;
    }
    input {
      border: #c7c7c7 solid 1px;
      text-align: center;
      height: 38px;
      width: 70px;
      border-radius: 8px;

    }
  }
</style>