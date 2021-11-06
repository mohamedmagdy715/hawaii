<template>
    <div class="container">
        <div>
            All rights reserved. Copyright &copy; 2021
        </div>
        <div class="links-container">
            <a href="#">Sitemap</a>
            <a href="#">Terms and conditions</a>
            <a href="#">Privacy</a>
            <a href="#">Help</a>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Footer',
}
</script>

<style scoped>
    .container{
        background-color: black;
        color: white;
        display: flex;
        justify-content: space-between;
        padding: 1% 5%;
    }
    a{
        color: white;
    }
    .links-container{
        width: 30%;
        display: flex;
        justify-content: space-between;
    }
    @media only screen and (max-width: 1100px) {
        .links-container{
            width: 50%;
        }
    }
    @media only screen and (max-width: 700px) {
        .container{
            flex-direction: column;
            align-items: center;
        }
        .links-container{
            width: 80%;
        }
    }
</style>