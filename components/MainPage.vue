<template>
  <v-app>
    <div :style="{'background-image':'url(/star_night_darken.jpg)', 'height':'180px'}">
      <v-main>
        <v-container class="maincont">
          <input class="search_field" placeholder="Поиск">
        </v-container>
      </v-main>
      <v-container class="container1">
        <v-list-item v-for='link in NineImages' :to="NineImages.url">
          <v-list-item-content>
            <v-img :class="NineImages[link.index].class" :src="NineImages[link.index].url" @click="goToImg(link)"></v-img>
          </v-list-item-content>
        </v-list-item>
      </v-container>
    </div>
  </v-app>
</template>

<script>
export default {
  name: 'MainPage',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      randoms1: '',
      NineImages: [],
      class: '',
    }
  },
  created() {
    this.RandomUnsplash()
  },
  methods: {
    goToImg(link){
      const route = this.$router.resolve({
        path: 'photos',
        query: {
          url: link.url,
          author_name: link.author_name,
          username: link.username,
          author_img: link.author_img
        }
      })
      this.$router.push(route.href)
    },
    async RandomUnsplash(){
      this.randoms1 = await this.$axios.$get('https://api.unsplash.com/photos/random',{
        params:{
          client_id: 'Vgp9ljcfWuPpxgo9NInVJXaj83ulmMt6bUdakr1JNxQ',
          count: 9
        }
      })
      for (let i = 0; i<this.randoms1.length; i += 1){
        this.NineImages.push({url: this.randoms1[i].urls.regular, index: i, class: this.getClass(i),
          author_name: this.randoms1[i].user.name, username: this.randoms1[i].user.username,
          author_img: this.randoms1[i].user.profile_image.large})
      }
      console.log(this.NineImages)
    },
    getClass(i){
      if(i===0){
        this.class = 'first'
      }
      else if(i===1){
        this.class = 'second'
      }
      else if(i===2){
        this.class = 'third'
      }
      else if(i===3){
        this.class = 'fourth'
      }
      else if(i===4){
        this.class = 'fifth'
      }
      else if(i===5){
        this.class = 'sixth'
      }
      else if(i===6){
        this.class = 'seventh'
      }
      else if(i===7){
        this.class = 'eights'
      }
      else if(i===8){
        this.class = 'nineth'
      }
      return this.class
    },
  }
}
</script>
<style>
.app-bar{
  background-color: black!important;
  box-shadow: none!important;
  height: 90px!important;
}
.mainlogo{
  max-width: 150px;
}
.favorite{
  max-width: 17px;
  margin-right: 6px;
}
.favorites{
  -webkit-text-fill-color: white;
  display: flex;
  align-items: center;
  font-size: 14px!important;
}
.container1 {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  gap: 0px 0px;
  grid-auto-flow: row;
  grid-template-areas:
    "first second third"
    "fourth fifth sixth"
    "seventh eights nineth";
  margin-top: 100px;
  max-width: 80%;
  width: fit-content;
}

.first {
  grid-area: first;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.second {
  grid-area: second;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.third {
  grid-area: third;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.fourth {
  grid-area: fourth;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.fifth {
  grid-area: fifth;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.sixth {
  grid-area: sixth;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.seventh {
  grid-area: seventh;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.eights {
  grid-area: eights;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.nineth {
  grid-area: nineth;
  border-radius: 15px;
  width: 300px;
  height: 300px;
}

.v-toolbar__content{
  display: flex;
  justify-content: space-around;
  height: 90px!important;
}
.v-main{
  margin-top: 74px!important;
  padding: 0px!important;
}
.maincont{
  display: flex;
  justify-content: center;
}
.search_field{
  border-radius: 35px;
  background-color: white;
  width: 40%;
  height: 35px;
  padding-left: 15px;
}
.randimg{
  max-width: 200px;
}
@media (max-width: 500px) {
  .container1{
    display: block;
  }
}
</style>
