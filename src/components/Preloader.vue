<template>
    <div id="preloader" v-show="show">
        <i class='layer'></i>
        <i class='layer'></i>
        <i class='layer'></i>
    </div>
</template>

<script>
export default {
    name: "Preloader",
    data() {
        return {
            show: true
        }
    },
    mounted() {
        setTimeout(() => {
            this.show=false
        },1000)
    }
}
</script>

<style scoped>
#preloader
    {
        background-color: #eee;
        width:100%;
        height: 100vh;
        display: grid;
        place-items: center;
        position: absolute;
        top:0%;
        left:0%;
    }

@-webkit-keyframes moveup
    {
      0%, 60%, 100%
          {
            -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
                    transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
          }
      25%
          {
            -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(1em);
                    transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(1em);
          }
    }
@keyframes moveup
    {
        0%, 60%, 100%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
            }
        25%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(1em);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(1em);
            }
    }
@-webkit-keyframes movedown
    {
        0%, 60%, 100%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
            }
        25%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(-1em);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(-1em);
            }
    }
@keyframes movedown
    {
        0%, 60%, 100%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(0);
            }
        25%
            {
                -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(-1em);
                transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg) translateZ(-1em);
            }
    }

.layer
    {
        display: block;
        position: absolute;
        height: 3em;
        width: 3em;
        box-shadow: 3px 3px 2px rgba(0, 0, 0, 0.2);
        -webkit-transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg);
              transform: rotateX(50deg) rotateY(0deg) rotateZ(45deg);
    }
.layer:nth-of-type(1)
    {
        background: #000;
        margin-top: 1.5em;
        -webkit-animation: movedown 1.8s cubic-bezier(0.39, 0.575, 0.565, 1) 0.9s infinite normal;
              animation: movedown 1.8s cubic-bezier(0.39, 0.575, 0.565, 1) 0.9s infinite normal;
    }
.layer:nth-of-type(1):before
    {
        content: '';
        position: absolute;
        width: 85%;
        height: 85%;
        background: #37332f;
    }
.layer:nth-of-type(2)
    {
        background: #5a96bc;
        margin-top: 0.75em;
    }
.layer:nth-of-type(3)
    {
        background: #eaa;
        -webkit-animation: moveup 1.8s cubic-bezier(0.39, 0.575, 0.565, 1) infinite normal;
              animation: moveup 1.8s cubic-bezier(0.39, 0.575, 0.565, 1) infinite normal;
    }
</style>