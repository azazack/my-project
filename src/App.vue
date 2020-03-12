<template lang="pug">
  div
    button(class="btn btn-secondary" @click.prevent="show") show
    modal(name="model-test" :min-height="200" height="auto")
      div.all
        div.containere
          p.head Edit Product Name
          span.product Product Quantity
          FontAwesomeIcon.close(:icon="['fas' ,'times']"  size="lg" @click.prevent="hide")
        pluss
        unity
        p.price Price/Unit
        div
          .marg
            pluss
            span &nbsp;  Per &nbsp;
            unity
          div(style="display:flex;flex-wrap:nowrap;")
            between(@parame="tests" ) &nbsp;
            div.cls(v-if="choice")
              pluss.button1
              span &nbsp; and &nbsp;
              pluss
              unity
            div.cls(v-if="!choice")
              pluss(:disabled="!choice")

</template>


<script lang="ts">
    import {Vue, Component} from "vue-property-decorator"
    import pluss from "@/components/PlusMinus.vue";
    import unity from "@/components/unity.vue";
    import between from "@/components/between.vue";
    import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
    import {library} from "@fortawesome/fontawesome-svg-core";
    import {faTimes,} from "@fortawesome/free-solid-svg-icons";

    library.add(faTimes);

    @Component({
        components:{pluss,unity,between,FontAwesomeIcon}
    })
    export default class Bigdal extends Vue {
        choice:boolean =true;
        show():void{
            this.$modal.show('model-test');
        }
        hide():void{
            this.$modal.hide('model-test');
        }
        tests(value){
        if(value==="between"){
            this.choice=true;
        }if(value=="more than"){
            this.choice=false;
            }
        }
    }

</script>

<style lang="scss">
  @import "stylesheets/variable";

  input[type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
  body{
    -webkit-user-select:none;
    -moz-user-select:none;
    -o-user-select:none;
    -user-select:none;
  }

  .all{
    padding: 0 0 70px 40px;
  .containere {
    padding: 30px 30px 30px 0;
  }
  .close{
    position: absolute;
    right: 20px;
    top: 20px;
    cursor: pointer;
  }

  .dlt{
    position: absolute;
    right: 20px;
    margin-top: 5px;
  }
  .product{
    position: absolute;
  }
  .price{
    margin: 10px 0 5px 0;
  }
    .marg{
      margin-bottom: 15px;
    }
.cls{
  height: 38px;
  display: inline-block;
  margin-left: 20px;
  .button1{
    margin-left: 10px;
  }
}

  }
</style>
