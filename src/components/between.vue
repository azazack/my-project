<template lang="pug">
  .TheInterface(v-on:click="toggled()")
    .holderr
      div.unity {{param}}
      FontAwesomeIcon.icone(:icon="['fas' ,'arrow-down']"  size="xs" )
      .TheHiden(v-if="isOpened")
        ul
          li(v-for="param in params" @click="emiiit(param)") {{param}}
</template>

<script lang="ts">
import {Vue,Component} from "vue-property-decorator";
import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
import {library} from "@fortawesome/fontawesome-svg-core";
import {faArrowDown} from "@fortawesome/free-solid-svg-icons";

library.add(faArrowDown);

@Component({
    components:{FontAwesomeIcon}
})
export default class Between extends Vue{
    params=['between','more than'];
    param="more than";
    isOpened=false;

    toggled(){
        this.isOpened=!this.isOpened
    }
    emiiit(value){
        this.param=value;
        this.$emit("parame",value)
    }

}
</script>

<style lang="scss">
  @import "../stylesheets/variable";
  .TheInterface {
    display: inline-block;
    border: black solid 1px;
    border-radius: 8px;
    height: 38px;
    width: 100px;
    margin-left: 3%;
    .holderr{
      position: relative;
      margin-top: 4px;
      margin-left: 4px;
    }
    .unity {
      display: inline;
    }

    .icone{
      position: absolute;
      right:10px;
      top: 6px;
    }
  }
  .TheHiden{
    margin-top: 9px;
    width: 100px;
    background-color: #2aa3ff;
    border-radius: 5px;
    margin-left: -4px;

    ul{
      padding: 0;
      text-align: center;
      li{
        list-style-type: none;
        transition:  0.3s;
      }
      li:hover{
        border: #212121 solid 1px;
        border-radius: 5px;
        cursor: pointer;
        opacity: 0.5;

      }

    }
  }


</style>