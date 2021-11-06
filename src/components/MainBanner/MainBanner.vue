<template>
    <div class="container">
        <div class="text-container">
            <p class="d1">What it's like to travel to Hawaii right now</p>
            <div class="d3">
                <p >Free flights to remote workers</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'MainBanner',
}
</script>

<style scoped>
    .container{
        color: white;
        background-image: linear-gradient(to right, rgba(0, 0, 0, 0.8), rgba(255, 255, 255, 0)),
                          url("../../assets/hawaiiCover.jpg");
        background-repeat: no-repeat;
        background-size: cover;
    }
    .text-container{
        width: 30%;
        padding: 4% 4%;
    }
    .d1{
        font-size: 4rem;
    }
    .d3{
        width: fit-content;
        border-top: 2px solid rgba(129, 129, 124, 0.5);
        font-size: 2rem;
    }
    @media only screen and (max-width: 1100px) {
        .text-container{
        width: 50%;
        }
    }
    @media only screen and (max-width: 800px) {
        .text-container{
        width: 70%;
        }
    }
    @media only screen and (max-width: 600px) {
        .text-container{
        width: 80%;
        }
    }
</style>