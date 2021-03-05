<template>
  <div class="home">
    <h2>
     Top Anime
    </h2>
    
    <b-container fluid>
      <b-row>
        <b-col cols="3" v-for="anime in animelist.top" :key="anime">
          <b-card
            style="color:Salmon"
            :img-src="anime.image_url"
            img-alt="Card image"
            img-height="550px"
            img-width="250px"
            img-top
          >
            <b-card-text>
              {{ anime.title }}
            </b-card-text>
          </b-card>

          <!-- {{ anime }} -->
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Home",
  props: {
    title: String,
    image: String,
  },
  components: {},
  data() {
    return {
      animelist: {},
    };
  },
  mounted() {
    axios({
      method: "GET",
      url: "https://jikan1.p.rapidapi.com/top/anime/1/upcoming",
      headers: {
        "x-rapidapi-key": "d070d378bbmshc8f19ecd0f7796dp11cf3djsn60b74ee1cda7",
        "x-rapidapi-host": "jikan1.p.rapidapi.com",
      },
    }).then((result) => {
      this.animelist = result.data;
      console.log(result);
    });
  },
};
</script>
<style>
.home {
  background: url(https://static.thairath.co.th/media/dFQROr7oWzulq5FZYRjc4ImSXkfZLyx7rZK9fVxucxzl4XBzcELOcGCpPHDBPeAELoO.jpg);
  width: 100%;
  height: 100%;
}
</style>
<style scoped>
h2 {
  color: #ffc300;
  font-size: 50px;
  font-weight: 200;
}
</style>
