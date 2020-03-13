<template lang="pug">
  .interface(v-on:click="toggled()")
    .holderr
      div.unity {{unity}}
      FontAwesomeIcon.icone(:icon="['fas' ,'arrow-down']"  size="xs" )
      .hiden(v-if="isOpened")
        ul
          li(v-for="unitie in unities" @click="emiiit(unitie)") {{unitie}}
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
export default class Unity extends Vue{
    unities=['kg','km','q'];
    unity="kg";
    isOpened=false;

    toggled(){
        this.isOpened=!this.isOpened
    }
    emiiit(value){
        this.unity=value;
    }

}
</script>

<style lang="scss">
  @import "../stylesheets/variable";
  .interface {
    display: inline-block;
    position: absolute;
    border: black solid 1px;
    border-radius: 8px;
    height: 38px;
    width: 85px;
    margin-left: 7px;
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
  .hiden{
    margin-top: 9px;
    width: 85px;
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