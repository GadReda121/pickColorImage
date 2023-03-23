<template>
    <div class="imageAttached">
        <img src="../../public/tinywow_MYIMAGE_10440821.jpg" alt="" />
        <input type="file" name="" id="" @change="showImg"/>
    </div>
</template>

<script>
export default {
    name: "ImageAttached",
    methods: {
        showImg() {
            const image = document.querySelector("img");
            const input = document.querySelector("input");
            image.src = URL.createObjectURL(input.files[0])
      }  
    },
    }
</script>

<style scoped>
    .imageAttached{
        display:grid;
        justify-content:center;
        grid-gap:20px;
    }
    input[type="file"]::file-selector-button {
        border: none;
        padding: 10px 30px;
        border-radius: 0.2em;
        background-color: #212529;
        color:#fff;
        transition: all .3s;
    }
    input[type="file"]::file-selector-button:hover {
        background-color: #212529;
        cursor:pointer;
    }
    img{
        height: 400px;
        /* width: 400px; */
        width:100%;
        margin:auto;
        border-radius: 20px;
        object-fit: cover;
        box-shadow:0px 0px 100px rgba(0,0,0,.1) 
    }
</style>