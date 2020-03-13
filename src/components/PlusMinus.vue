<template lang="pug">
  .button
    button(v-on:click="minuss()" class="btn" :disabled="disabled") -
    input.inpt(type="number" v-model="newvalue" onkeypress="return event.charCode >=48" :disabled="disabled" )
    button(v-on:click="pluss()" class="btn" :disabled="disabled" ) +
</template>

<script lang="ts">
 import {Vue,Component,Prop} from "vue-property-decorator";
@Component({})
 export default class Pluss extends Vue {
    @Prop({default: '1'}) min: number;
    @Prop({default: '20'}) max: number;
    @Prop() disabled?: boolean;

    newvalue: number = 1;

    minuss(valeurm) {
        if ((this.newvalue) > this.min) {
            this.newvalue--;
        }
        this.newvalue=valeurm;
        this.$emit('pm',valeurm)
    }

    pluss(valeurp) {
        if ((this.newvalue) < this.max) {
            this.newvalue++;
        }
        this.newvalue = valeurp;
        this.$emit('pm', valeurp)
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