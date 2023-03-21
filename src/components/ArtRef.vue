<script setup>
import { ref } from 'vue';
let urlbase = 'https://www.reddit.com/r/'
let urlend = '/.json'

const images = ref([])

async function loadImagesFromSub(sub){
    let url = urlbase + sub + urlend;
    let subImgs = [];
    fetch(url).then(res => res.json()).then(d =>{
        if(!d.data){return}
        d.data.children.forEach(c=>{
            subImgs.push(c.data.url);
        })
    })
    // this.subImgs = subImgs;
    // console.log(this.subImgs)
    return subImgs;
}
async function getImages(){
    this.loadImagesFromSub('mombod').then(s => {
        images.value = s;
        console.log(s);
        return s
    })
}
</script>

<template>
    <h1>lol</h1>
    <button @click="getImages()"></button>
    <div v-for="img in images" :key="img">
        <img :src="img"/>
    </div>
</template>

<style scoped>

</style>
