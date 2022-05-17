<template>
  <HomeHeader />
  <WindowPortal>
    <template v-slot:header><div class="header">Introduction to TestView</div></template>
    <SlideContainer v-model:activeSlideId="this.$store.getters.getIndexSlideSelected">
        <Slide slideId="0" name="First Slide">

        </Slide>
    </SlideContainer>
  </WindowPortal>
</template>
<script>
  import { Slide, SlideContainer } from "../DefaultSlide/DefaultSlide";
  import WindowPortal from "../layouts/WindowPortal.vue";
  import HomeHeader from "../layouts/HomeHeader.vue"
  import BaseQuestionButton from "../UI/BaseQuestionButton.vue";
  import BaseQuestion from "../UI/BaseQuestion.vue"
  import BaseTermButton from "../UI/BaseTermButton.vue"
  import BaseQuestionImage from "../UI/BaseQuestionImage.vue"
  export default {
    components: { Slide, SlideContainer, WindowPortal, HomeHeader, BaseQuestionButton, BaseQuestion, BaseTermButton, BaseQuestionImage },
    methods: {
    checkSlideIndex(){
        this.activeSlideId = this.$store.getters.getIndexSlideSelected;
        return this.activeSlideId.toString();
    },
  },
    data() {
      return {
        activeSlideId: this.$store.getters.getIndexSlideSelected.toString(),
        activeTermId: this.$store.getters.getActiveTermId
      };
    },
  };
</script>
<style scoped>
 @import '../../assets/introduction.css';
</style>
