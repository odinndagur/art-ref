<script setup>
import { onMounted, ref } from 'vue';
let urlbase = 'https://www.reddit.com/r/'
let urlend = '/.json'

const images = ref([])

function isImgUrl(url) {
  return /\.(jpe?g|png|webp|avif|gif)$/.test(url)
}

async function loadImagesFromSub(sub){
    let url = urlbase + sub + urlend;
    fetch(url).then(res => res.json()).then(d =>{
        if(!d.data){return}
        d.data.children.forEach(c=>{
            let imgUrl = c.data.url
            if(isImgUrl(imgUrl)){
                images.value.push(c.data.url);
            }
        })
    })
}
async function getImages(){
    loadImagesFromSub('mombod')
}

onMounted(() => {
    getImages()
})
</script>

<template>
    <h1>lol</h1>
    <button @click="getImages()"></button>
    <div class="images">
        <div v-for="img in images" :key="img">
            <img :src="img" class="image"/>
        </div>
    </div>
</template>

<style scoped>
.image {
    max-width: 600px;
    margin: auto;
    padding: 0.5rem 2rem;
}

.images {
    /* width: 100vw;
    padding: 0 2rem;
    margin: auto;
    display: flex;
    flex-direction: column; */
    /* justify-content: center;
    align-items: center; */
    /* background-color: red; */
}
</style>
