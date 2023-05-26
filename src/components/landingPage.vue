<template>
    <div class="appContainer">
      <signIn />
      <titleMain />
      <animateDiv />
    </div>
  </template>
  
  <script>
  import signIn from './signIn.vue'
  import titleMain from './titleMain.vue'
  import animateDiv from './animateDiv.vue';
  
  export default {
    name: 'landingPage',
    components: {
      signIn,
      titleMain,
      animateDiv
    }
  }
  </script>
  
  <style>
  @font-face {
    font-family: "ComicsDeluxe";
    src: url("/Users/mac/Desktop/trandandan/src/assets/ComicsDeluxe.ttf");
  }
  body {
    margin: 0;
  }
  .appContainer {
    left: 0px;
    top: 0px;
    height: 100vh;
    width: 100vw;
    font-family: "ComicsDeluxe";
    background: url("/Users/mac/Desktop/trandandan/src/assets/pxfuel.jpg");
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
      -webkit-box-align: center;
      -ms-flex-align: center;
      align-items: center;
      display: -webkit-box;
      display: -ms-flexbox;
      display: flex;
      font-size: 1rem;
      -webkit-font-smoothing: antialiased;
      -moz-osx-font-smoothing: grayscale;
      text-align: center;
      color: #2c3e50;
  }
  </style>
  
  