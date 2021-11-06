<template>
  <div class="menu-container">
    <div @click="nav('sectionOne')" id="item1" >Section 1</div>
    <div @click="nav('sectionTwo')" id="item2">Section 2</div>
    <div @click="nav('sectionThree')" id="item3">Section 3</div>
  </div>
</template>

<script>
export default {
  name: "Menu",
  data: ()=>{
      return{
          sectionOneOffsetTop : 0,
          sectionTwoOffsetTop : 0,
          sectionThreeOffsetTop : 0
      }
  },
  methods: {
    nav: (to) => {
      const position =
        document.getElementById(to).offsetTop -
        document.getElementById("menu").offsetHeight;
      // smooth scroll
      window.scrollTo({ top: position, behavior: "smooth" });
    },
    handleScroll: function(){
        let docScroll = document.documentElement.scrollTop;
        this.sectionOneOffsetTop = document.getElementById("sectionOne").offsetTop  - document.getElementById("menu").offsetHeight;
        this.sectionTwoOffsetTop = document.getElementById("sectionTwo").offsetTop - document.getElementById("menu").offsetHeight;
        this.sectionThreeOffsetTop = document.getElementById("sectionThree").offsetTop - document.getElementById("menu").offsetHeight;
        document.querySelectorAll(".menu-container>div").forEach((item)=>{
            item.classList.remove("active")
        })
        if ( (docScroll >= this.sectionOneOffsetTop - 100) && (docScroll < this.sectionTwoOffsetTop )){
            document.getElementById("item1").classList.add("active")
        }else if((docScroll >= this.sectionTwoOffsetTop) && (docScroll < this.sectionThreeOffsetTop )){
            document.getElementById("item2").classList.add("active")
        }else if( docScroll >= this.sectionThreeOffsetTop){
            document.getElementById("item3").classList.add("active")
        }
    }
  },
  mounted() {
        document.addEventListener("scroll", debounce(this.handleScroll, 100,false));

        function debounce(func, wait, immediate) {
            let timeout;

            return function executedFunction() {
                let context = this;
                let args = arguments;

                let later = function () {
                timeout = null;
                if (!immediate) func.apply(context, args);
                };

                let callNow = immediate && !timeout;

                clearTimeout(timeout);

                timeout = setTimeout(later, wait);

                if (callNow) func.apply(context, args);
            };
        }
  },
};
</script>

<style scoped>
.menu-container {
  position: sticky;
  z-index: 10;
  top: 0;
  display: grid;
  grid-template: 1fr / repeat(3, 1fr);
  background-color: white;
  border-bottom: 1px solid rgba(129, 129, 124, 0.5);
}
.menu-container > div {
  color: rgb(112, 112, 112);
  padding: 5% 0;
  text-align: center;
  font-size: 20px;
  cursor: pointer;
}
.active {
  color: rgb(10, 82, 123) !important;
  border-bottom: 5px solid rgb(10, 82, 123);
  font-weight: bolder;
}
@media only screen and (max-width: 600px) {
  .menu-container {
    grid-template: repeat(3, 1fr) / 1fr;
  }
  .menu-container > div {
    padding: 2% 0;
  }
}
</style>
