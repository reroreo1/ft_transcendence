<template>
    <a id="but" href="#" @click="redirection">
        <span></span>
        <span></span>
        <span></span>
        <span></span>
        Sign in
    </a>
</template>

<script>
    export default{
        methods:{
            redirection(){
                alert("hello there");
            }
        }
    }
</script>

<style>
:root {
    font-size: calc(1vw + 1vh + 1.5vmin);
}
    #but{
    top: 60%;
    left: 15%;
    text-align: center;
    color: #fff;
    text-shadow:
      0 0 5px #dadada,
      0 0 10px #dadada,
      0 0 20px #000,
      0 0 40px #dadada,
      0 0 80px #dadada,
      0 0 90px #dadada
    }
  a {
    position: absolute;
    padding: 25px 30px;
    margin: 10px 0;
    text-decoration: none;
    text-transform: uppercase;
    transition: 0.5s;
    letter-spacing: 4px;
    overflow: hidden;
    margin-right: 50px;
}
  
  a:hover {
    background: #fff;
    color: #000;
    box-shadow: 0 0 5px #ffffff,
        0 0 25px #ffffff,
        0 0 50px #ffffff,
        0 0 200px #ffffff;
  }
</style>