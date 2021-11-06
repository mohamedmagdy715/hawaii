<template>
  <div id="app">
    <MainBanner />
    <Menu id="menu"/>
    <div id="sections">
      <section-one id="sectionOne"/>
      <section-two id="sectionTwo"/>
      <section-three id="sectionThree"/>
    </div>
    <Footer />
  </div>
</template>

<script>
import MainBanner from './components/MainBanner/MainBanner.vue';
import Menu from './components/Menu/Menu.vue';
import SectionOne from './components/SectionOne/SectionOne.vue';
import SectionThree from './components/SectionThree/SectionThree.vue';
import SectionTwo from './components/SectionTwo/SectionTwo.vue';
import Footer from './components/Footer/Footer.vue';

export default {
  name: 'App',
  components: {
    MainBanner,
    Menu,
    SectionOne,
    SectionTwo,
    SectionThree,
    Footer
  }
}
</script>

<style>
  #app{
    margin: -8px;
    background-color: rgb(248, 248, 248);
  }
  #sections{
    padding: 0 5%;
  }
</style>
