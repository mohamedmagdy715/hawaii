<template>
    <div class="container">
        <div class="image">
            <img src="../../assets/rainbow-fish-91663.jpg" alt="rainbow-fish">
        </div>
        <div class="title">Section 1</div>
        <div class="text-container">
            <span class="points">Population</span>
            <span class="item7">Total ({{population}}), Rank({{rank}})</span>
            <span class="points">Dimensions</span>
            <span class="item8">Length {{lengthMi}} mi ({{lengthKm}} km), Width n/a mi (n/a km)</span>
            <span class="points">Language</span>
            <span class="item9">Official Languages English, Hawaiian</span>
            <span class="points">Largest city</span>
            <span class="item10">The capital ({{capital}})</span>
            <span class="points">Largest metro</span>
            <span class="item11">The largest metro in Island of O'ahu</span>
            <span class="points">Elevation</span>
            <span class="item12">Highest elevation {{elevationFt}} ft ({{elevationM}} m)</span>
        </div>
    </div>
</template>

<script>
export default {
  name: 'SectionOne',
  data: ()=>{
      return{
          population : "1,415,872",
          rank : "40th",
          lengthMi : "1,522",
          lengthKm : "2,450",
          widthMi : "n/a",
          widthKm : "n/a",
          capital : "Honolulu",
          elevationFt : "13,796",
          elevationM : "4,205"
      }
  }
}
</script>

<style scoped>
    .container{
        height: fit-content;
        display: grid;
        grid-template: 15% auto / 50% 15% auto;
        padding: 5% 0;
        column-gap: 3%;
        border-bottom: 1px solid rgba(129, 129, 124, 0.5);
    }
    .image{
        height: fit-content;
        grid-column: 1 /2;
        grid-row: 1 /3;
    }
    img{
        width: 100%;
        height: auto;
        border-radius: 2%;
    }
    .title{
        grid-column: 2 /4;
        grid-row: 1 /2;
        font-weight: bolder;
        font-size: 2rem;
    }
    .text-container{
        margin-top: 3%;
        grid-column: 2 / 4;
        grid-row: 2 / 3;
        display: grid;
        grid-template: repeat(6, 1fr) / 1fr 2fr;
        font-size: 1.25rem;
        row-gap: 5px;
    }
    .points{
        color: rgb(112, 112, 112);
        font-weight: bold;
    }
    .item7{
        grid-column: 2 / 3;
        grid-row: 1 / 2;
    }
    .item8{
        grid-column: 2 / 3;
        grid-row: 2 / 3;
    }
    .item9{
        grid-column: 2 / 3;
        grid-row: 3 / 4;
    }
    .item10{
        grid-column: 2 / 3;
        grid-row: 4 / 5;
    }
    .item11{
        grid-column: 2 / 3;
        grid-row: 5 / 6;
    }
    .item12{
        grid-column: 2 / 3;
        grid-row: 6 / 7;
    }
    @media only screen and (max-width: 1200px) {
        .container{
            grid-template: 15% auto / 40% 25% auto;
        }
    }
    @media only screen and (max-width: 800px) {
        .container{
            grid-template: 10% auto 50% / 1fr;
        }
        .image{
            grid-column: 1 /2;
            grid-row: 2 /3;
            /* width: 50%; */
            margin: auto;
        }
        .title{
            grid-column: 1 /2;
            grid-row: 1 /2;
        }
        .text-container{
            margin-top: 5%;
            grid-column: 1 / 2;
            grid-row: 3 / 4;
            margin-bottom: 15%;
        }
    }
    @media only screen and (max-width: 700px) {
        .text-container{
            margin-bottom: 5%;
        }
    }
</style>