<script setup lang='ts'>


</script>

<template>
    <div class="container">
        <p>Lay down and relax in one of our state of the art unique staterooms.
        </p>
    </div>
</template>

<style scoped>

    .container {
        position: absolute;
        background-image: url('./../assets/bedroom.png');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        border-radius: 1rem;
        top: 35rem;
        width: 90vw;

        margin-left:1%;
        min-height: 300px;
        display: flex;
        flex-direction: row;
        overflow: hidden;
    }
.container::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  background: linear-gradient(
    to right,
    #21354700 0%,
    rgba(33, 53, 36, 0.25) 25%,
      rgb(36, 36, 36) 60%,
    rgb(36, 36, 36) 100%
  );
  z-index: 1;
}
    img {
        height: 30rem;

        border-radius: 1rem;
    }

    p {
        font-family:'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif, Helvetica, sans-serif;
        font-weight: 400;
        font-size: x-large;
        margin-right: 20px;
        margin-left: 70%;
z-index: 2;
    }

    @media (max-width: 600px) {
        .container {
            position: absolute;
            background-image: url('./../assets/bedroom.png');
            background-size: cover;
                 top: 35rem;
            margin-left: auto;
            width: 100vw;
            display: flex;
            left: 0px;
                    overflow: hidden;
        }
.container::before {
  content: "";


  width: 100%;
  height: 100%;
  pointer-events: none;
  background: linear-gradient(
    to top,
    #21354700 0%,
    rgba(33, 53, 36, 0.25) 50%,

    rgb(36, 36, 36) 100%
  );
  z-index: 1;
}
        img {
            position: relative;
            width: auto;

            left: 0;
            outline: 0cap;
        }
    }
</style>