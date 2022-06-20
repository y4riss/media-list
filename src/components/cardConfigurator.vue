<template>
  <div>
          <ControlCards @uploadImgBackground="uploadImgBackground" @addCard="addCard" @changeCardWidth="changeCardWidth" @changeBackground="changeBackground" @handleMouseLeave="handleMouseLeave"></ControlCards>
          <ControlCard v-if="options.focusOn != null" @changeCardOrder="changeCardOrder" @changeCardBackground="changeCardBackground"  @handleCardButton="handleCardButton" @uploadImg="uploadImg" @handleBorder="handleBorder" @handleBorderStyle="handleBorderStyle" @handleShadowBtn="handleShadowBtn" @handleShadow="handleShadow" :options="options"></ControlCard>
          <ControlButton v-if="options.focusOn != null" @changeButtonSize="changeButtonSize"  @changeButtonColor="changeButtonColor" @toggleOutline="toggleOutline" />
          <ControlText v-if="options.showControlText!=null" @changeText="changeText" @changeWeight="changeWeight" @changetextColor="changetextColor" @changeFontSize="changeFontSize"></ControlText>
          <ControlInputText v-if="options.focusOn != null"  :options="options" ></ControlInputText>
  </div>
</template>

<script>
import ControlCards from "./cardComponents/ControlCards.vue";
import ControlCard from "./cardComponents/ControlCard.vue";
import ControlText from "./cardComponents/ControlText.vue";
import ControlButton from "./cardComponents/ControlButton.vue";
import ControlInputText from "./cardComponents/ControlInputText.vue";

export default {

    props : ["options"],
    components : {
    ControlCards,
    ControlCard,
    ControlText,
    ControlButton,
    ControlInputText
    },
    methods : {
          changeText(a) {
            this.$emit('changeText',a) ;
        },
        changeWeight(a){
          this.$emit('changeWeight',a)
        },
        changetextColor(a){
          this.$emit('changetextColor',a);
        },
        changeFontSize(a){
          this.$emit('changeFontSize',a);
        },


        //button
         changeButtonSize(s){
            this.$emit('changeButtonSize',s);
        },
        changeButtonColor(btsClr){
    
            this.$emit('changeButtonColor',btsClr) ;
        },
        toggleOutline(){
            this.$emit('toggleOutline') ;
        },

        //single card

         changeCardOrder(a){
            this.$emit('changeCardOrder',a);
        },
        changeCardBackground(a){
            this.$emit('changeCardBackground',a)
        },
        handleCardButton(action){
            this.$emit('handleCardButton',action)
        },
        uploadImg(e){
             this.$emit('uploadImg',e)
        },
        handleBorder(e,type){
            this.$emit('handleBorder',e,type)
        },
        handleBorderStyle(style){
             this.$emit('handleBorderStyle',style)
        },
        handleShadowBtn(e){
        this.$emit('handleShadowBtn',e)

        },
        handleShadow(e,option){
        this.$emit('handleShadow',e,option)
        },

        //all cards
         addCard () {
            this.$emit('addCard') ;
        },
        changeBackground(e){
            this.$emit('changeBackground',e)
        },
        changeCardWidth (width,e){
            this.$emit('changeCardWidth',width,e)
        },
        handleMouseLeave(e){
            this.$emit('handleMouseLeave',e)
        },
        uploadImgBackground(e){
             this.$emit('uploadImgBackground',e)
        },
    },

    }

</script>
