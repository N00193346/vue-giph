<template>
    <div>
        <b-card-group columns>
        <b-card
            v-for="gif in gifs"
            :key="gif.id"
            :img-src="gif.images.fixed_width.url"
        >


            <b-card-text>
                <a :href="gif.url" target="_blank">{{gif.title}}</a>
            </b-card-text>
        </b-card>
        </b-card-group>

    </div>
</template>
<script>
import axios from 'axios';
const API_KEY = "DHBB9fly7G28uAUsm5ZyixCi3PmHtGMf";
const GIPHY_URL = "https://api.giphy.com/v1/gifs"
export default {
    name: 'GiphyViewer',
    data() {
        return {
            gifs: [],

        };
    },
    mounted() {
      
        axios.get(`${GIPHY_URL}/trending?api_key=${API_KEY}`)
             .then((response) => {
                 console.log(response.data.data)
                 this.gifs = response.data.data;
             } )
             .catch(error => console.log(error))
    },

    method: {

    },
    
}
</script>
<style scoped>

</style>
