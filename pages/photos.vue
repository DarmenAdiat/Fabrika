<template>
  <div :style="{'background-image':'url(/Adam.jpg)', 'height':'700px'}">
    <v-main style="margin-top: 0px!important;">
      <v-container class="containerMain">
        <div class="Author"><div style="display: flex!important;"><v-img class="authorimg" :src="this.author_img"></v-img>
          <p class="user" >{{ this.author_name }} <br>@{{ this.username }}</p></div>
          <div >
            <v-btn style="height: 40px; width: 40px!important; min-width: 0px!important;margin-right: 5px!important;"><v-img class='favor' src="/heart-black.svg"></v-img></v-btn>
            <v-btn class="downbut" style="height: 40px; background-color: #FFF200; min-width: 0px"><v-img class='favor' src="/download.png"></v-img><mik class="mik">Download</mik></v-btn>
          </div>
        </div>
        <div class="ImgCenter">
          <v-img class="MainImg" :src="this.UrlOfUnsplash"></v-img>
        </div>
      </v-container>
    </v-main>
  </div>
</template>

<script>
export default {
  name: "photos",
  data: () => ({
    UrlOfUnsplash: '',
    author_name: '',
    username: '',
    author_img: ''
  }),
  created() {
    this.initialize()
  },
  methods:{
    async initialize() {
      this.UrlOfUnsplash = this.$route.query.url,
      this.author_name = this.$route.query.author_name,
      this.username = this.$route.query.username,
      this.author_img = this.$route.query.author_img
    }
  }
}
</script>

<style>
.maincont{
  display: flex;
  justify-content: center;
}
.containerMain {
  display: grid;
  margin-top: 80px;
  justify-content: center;
  flex-direction: column;
  grid-template-columns: 1fr;
  grid-template-rows: 0.3fr 1.7fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    "Author"
    "ImgCenter";
  max-width: fit-content;
}
.Author {
  grid-area: Author;
  display: flex;
  justify-content: space-between;
}
.authorimg{
  max-width: 50px;
  max-height: 50px;
  border-radius: 3px;
  border-color: white;
  border-style: inset;
}
.ImgCenter {
  grid-area: ImgCenter;
  margin-top: 20px;
  height: fit-content;
}
.MainImg{
  border-radius: 7px;
}
.user{
  -webkit-text-fill-color: white;
  margin-left: 7px;
}
.favor{
  max-width: 17px;
}
@media (max-width: 500px) {
  .containerMain{
    display: block;
  }
  .mik{
    display: none;
  }
  .downbut{
    width: 40px;
  }
}

</style>
