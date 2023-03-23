<template>
    <div class="imageAttached">
        <p class="d-flex align-items-center justify-content-center">
            <h6 @copy="pasteColor"></h6>
            <font-awesome-icon icon="fa-solid fa-paste" size="2xl" class="icon" style="color: #ffffff;cursor:pointer;" @click="pasteColor" v-show="show"/>
        </p>
        <img src="../../public/image.png" alt="ImagePicked" />
        <input type="file" @change="showImg" accept="image/*" />
        <button type="button" @click="showColor">Pick Color</button>
    </div>
</template>

<script>
import Swal from 'sweetalert2';

export default {
    name: "ImageAttached",
    data() {
        return {
            show: false
        }
    },
    mounted(){
        const button = document.querySelector("button");
        const pickColor = async () => {
            const eyeDropper = new EyeDropper();
            const { sRGBHex } = await eyeDropper.open();
            const p = document.querySelector("p");
            const h6 = document.querySelector("h6");
            h6.innerHTML = sRGBHex;
            p.style.backgroundColor= `${sRGBHex}`;
        }
        button.addEventListener("click", pickColor);
    },
    methods: {
        showImg() {
            const image = document.querySelector("img");
            const input = document.querySelector("input");
            image.src = URL.createObjectURL(input.files[0]);
        },
        showColor(){
            this.show = true;
        },
        pasteColor(){
            const h6 = document.querySelector("h6");
            navigator.clipboard.writeText(h6.firstChild.textContent);
            const Toast = Swal.mixin({
                toast: true,
                position: 'top-end',
                showConfirmButton: false,
                timer: 3000,
                timerProgressBar: true,
                didOpen: (toast) => {
                    toast.addEventListener('mouseenter', Swal.stopTimer)
                    toast.addEventListener('mouseleave', Swal.resumeTimer)
                }
            })
            Toast.fire({
                icon: 'success',
                title: `Color Copied &#128522;`
            })
        }
    }
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
        padding: 20px 30px;
        border-radius: 0.2em;
        /* background-color: #eaa; */
        background: #000;
        color:#fff;
        transition: all .3s;
        box-shadow:0px 0px 20px rgba(0,0,0,.1);
        width:100%;
    }
    input[type="file"]::file-selector-button:hover {
        cursor:pointer;
    }
    button{
        border: none;
        padding: 20px 30px;
        border-radius: 0.2em;
        /* background-color: #eaa; */
        background: linear-gradient(45deg, #eaa,#eae,#aae);
        color:#fff;
        transition: all .3s;
        box-shadow:0px 0px 20px rgba(0,0,0,.1);
        width:100%;
        text-shadow: 0 0 20px black;
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
    p{
        color:#fff;
        text-align:center;
        padding:20px 0px;
        position: relative;
        border-radius: 5px;
        box-shadow: 0 0 1px rgba(0,0,0,.1);
        margin-bottom: 0;
    }
    h6{
        text-align:center;
        margin-top:5px;
        text-shadow:0 0 50px #000;
        font-family: 'Roboto', sans-serif;
    }
    .icon{
        position:absolute;
        right:0px;
        background-color:#000;
        padding:20px;
        border-radius: 5px;
    }
</style>