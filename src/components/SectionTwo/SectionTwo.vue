<template>
  <div class="container">
    <div class="title">Section 2</div>
    <div class="years">
      <ul>
        <li v-for="(year, index) in years" :key="year.year">
          <div v-bind:class = "(index == 0)?'bullet active big':'bullet'" >
            <svg v-if="index == 0" aria-hidden="true" viewBox="0 0 32 32" focusable="false" class="white" >
              <path
                d="M16 4c6.6 0 12 5.4 12 12s-5.4 12-12 12S4 22.6 4 16 9.4 4 16 4zm0-4C7.2 0 0 7.2 0 16s7.2 16 16 16 16-7.2 16-16S24.8 0 16 0z"
              ></path>
              <circle cx="16" cy="16" r="6"></circle>
            </svg>
            <svg v-else aria-hidden="true" viewBox="0 0 32 32" focusable="false">
              <circle stroke="none" cx="16" cy="16" r="10"></circle>
            </svg>
          </div>
          <span v-bind:class = "(index == 0)?'first-active year-text':'year-text'"  @click="addActive($event)">
            {{year.year}}
            <i class="fas fa-long-arrow-alt-right" v-bind:class = "(index == 0)?'i-active':''" ></i>
            <p class="year-content" v-bind:class = "(index == 0)?'':'content-inactive'">
              {{year.content}}
            </p>
          </span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
  const lorem = "Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequatur repudiandae praesentium corrupti necessitatibus, sit odio vero consequuntur labore. Ratione itaque, harum distinctio voluptas odio ea et aperiam aspernatur quis sequi.";
  export default {
    name: "SectionTwo",
    data : ()=>{
      return{
        years : [
          {
            year : "1778",
            content : lorem
          },
          {
            year : "1779",
            content : lorem
          },
          {
            year : "1789",
            content : lorem
          },
          {
            year : "1820",
            content : lorem
          },
          {
            year : "1830",
            content : lorem
          }
        ]
      }
    },
    methods : {
      addActive : (e)=>{
        document.querySelectorAll(".year-text").forEach((span)=>{
          span.style.fontSize = "25px"
          span.querySelector("i").style.display = "inline"
          span.querySelector("p").style.display = "none"
        })
        e.target.querySelector("i").style.display = "none"
        e.target.querySelector("p").style.display = "block"
        e.target.style.fontSize = "35px";
        let bullets = document.querySelectorAll(".bullet");
        bullets.forEach((bullet)=>{
          bullet.classList.remove("active")
        })
        e.target.parentElement.firstChild.classList.add("active")
        for (const bullet of bullets) {
          if(bullet.classList.contains("active")){
            bullet.classList.add("big");
            bullet.innerHTML = 
                  `<svg aria-hidden="true" viewBox="0 0 32 32" focusable="false" style="border-radius: 50%; background-color : white" class="white" >
                    <path
                      d="M16 4c6.6 0 12 5.4 12 12s-5.4 12-12 12S4 22.6 4 16 9.4 4 16 4zm0-4C7.2 0 0 7.2 0 16s7.2 16 16 16 16-7.2 16-16S24.8 0 16 0z"
                    ></path>
                    <circle cx="16" cy="16" r="6"></circle>
                  </svg>`
          }
          else{
            bullet.classList.remove("big");
            bullet.innerHTML = 
            `<svg aria-hidden="true" viewBox="0 0 32 32" focusable="false">
              <circle stroke="none" cx="16" cy="16" r="10"></circle>
            </svg>`
          }
        }
      }
    }
  };

</script>

<style scoped>
  *{
    transition: all 0.5s ease-out;
  }
  .first-active{
    font-size: 35px;
  }
  .i-active{
    display: none;
  }
  .content-inactive{
    display: none;
  }
  .container {
    padding: 5% 0 0 ;
    border-bottom: 1px solid rgba(129, 129, 124, 0.5);
  }
  .white{
    background-color: white;
    border-radius: 50%;
  }
  .title {
    font-weight: bolder;
    font-size: 2rem;
  }
  .years{
    font-size: 25px;
    font-family: 'Merriweather', serif;
    color: rgb(10, 82, 123);
    margin-top: 5%;
  }
  .year-content{
    font-size: 15px;
    color: black;
    margin: 1% 0 0 3%;
  }
  /* No normal bullets */
  ul {
    list-style-type: none;
  }

  li {
    /* turn on relative positioning so the line is placed relative to the item rather than absolutely on the page */
    position: relative;
    
    /* padding to space things out rather than margins as the line would get broken up otherwise */
    margin: 0;
    padding-bottom: 1.5em;
    padding-left: 0px;
    font-size: 25px;
  }

  /* The actual line being placed before each list item */
  li:before {
    background-color: rgb(163, 163, 163); 
    width: 1px;
    content: '';
    position: absolute;
    top: 0;
    bottom: 0px;
    left: 4.5px;
  }
      
  /* Start the line further down on the first list item */
  li:first-child:before { 
    top: 22px;  
  }

  /* Stop the line short on the final list item */
  li:last-child:before {
    height: 20px; 
  }
      
  /* Styles for the SVG bullet points */
  .bullet { 
    width: 10px; 
    fill:rgb(163, 163, 163); 
    float: left; 
    padding-right: 10px;
    position: relative;
  }
  .bullet.big { 
    width: 20px; 
    margin-left: -5px; 
    padding-right: 8px; 
    fill:rgb(10, 82, 123);
  }
  li>span{
    cursor: pointer
  }
</style>
