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
        div(v-for="(tes,index) in testing" :key="tes" )
          .marg
            pluss(v-model="tes.class1")
            span(v-model="tes.class2") &nbsp;  Per &nbsp;
            unity(v-model="tes.class3")
          div(style="display:flex;flex-wrap:nowrap;" v-model="tes.class4")
            between(@parame="tests" v-model="tes.class5" ) &nbsp;
            div.cls(v-if="choice" v-model="tes.class6")
              pluss.button1(v-model="tes.class7")
              span(v-model="tes.class8") &nbsp; and &nbsp;
              pluss(v-model="tes.class9")
              unity(v-model="tes.class10")
            div.cls(v-if="!choice" v-model="tes.class11")
              pluss(:disabled="!choice" v-model="tes.class12")
          FontAwesomeIcon.dlt(:icon="['fas' ,'trash-alt']"  size="lg" v-on:click="removee(index)")
          hr(class="down" size="30" )
        button(class="btn btn-primary btn-lg" v-on:click="showing") add next price
</template>

<script lang="ts">
    import {Vue, Component} from "vue-property-decorator"
    import pluss from "@/components/PlusMinus.vue";
    import unity from "@/components/unity.vue";
    import between from "@/components/between.vue";
    import {FontAwesomeIcon} from "@fortawesome/vue-fontawesome";
    import {library} from "@fortawesome/fontawesome-svg-core";
    import {faTimes, faTrashAlt} from "@fortawesome/free-solid-svg-icons";

    library.add(faTimes,faTrashAlt);

    @Component({
        components: {pluss, unity, between, FontAwesomeIcon}
    })
    export default class Bigdal extends Vue {
        choice: boolean = false;
        testing = [{
            class1: "",
            class2: "",
            class3: "",
            class4: "",
            class5: "",
            class6: "",
            class7: "",
            class8: "",
            class9: "",
            class10: "",
            class11: "",
            class12: "",
        }];

        show(): void {
            this.$modal.show('model-test');
        }

        hide(): void {
            this.$modal.hide('model-test');
        }

        tests(value) {
            if (value === "between") {
                this.choice = true;
            }
            if (value == "more than") {
                this.choice = false;
            }
        }

        showing() {
            this.testing.push({
                class1: "",
                class2: "",
                class3: "",
                class4: "",
                class5: "",
                class6: "",
                class7: "",
                class8: "",
                class9: "",
                class10: "",
                class11: "",
                class12: "",

            })


        }
        removee(index){
            console.log(index);
            this.testing.splice(index,1)
        }
    }

</script>

<style lang="scss">
  @import "stylesheets/variable";
  @import "~bootstrap/scss/_buttons.scss" input

  [type=number]::-webkit-inner-spin-button,
  input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  body {
    -webkit-user-select: none;
    -moz-user-select: none;
    -o-user-select: none;
    -user-select: none;
  }

  .all {
    padding: 0 40px 70px 40px;

    .containere {
      padding: 30px 30px 30px 0;
    }

    .close {
      position: absolute;
      right: 20px;
      top: 20px;
      cursor: pointer;
    }

    .dlt {
      position: absolute;
      right: 40px;
      margin-top: -15px;
    }

    .product {
      position: absolute;
    }

    .price {
      margin: 10px 0 5px 0;
    }

    .marg {
      margin-bottom: 15px;
    }

    .cls {
      height: 38px;
      display: inline-block;
      margin-left: 20px;

      .button1 {
        margin-left: 10px;
      }
    }

    .down {
      margin-top: 15px;

    }

  }
</style>
