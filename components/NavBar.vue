<template>
  <v-app-bar
    class="app-bar"
    fixed
    app>
    <v-img class='mainlogo' src="/main_logo.png" @click="goHome"></v-img>
    <div class="favorites">
      <v-img class='favorite' src="/heart-white.svg"></v-img>
      <a href="/Favorite" style="text-decoration: none; -webkit-text-fill-color: white"><sol class="sol">Избранное</sol></a>
    </div>
  </v-app-bar>
</template>

<script>
export default {
  name: "NavBar",
  computed: {
    links() {
      return [
        {icon: 'mdi-login', text: 'Избранное', route: '/Favorite'},
      ]
    },
  },
  methods: {
    gotoFav() {
      this.$router.push('/Favorite')
    },
    goHome(){
      this.$router.push('/').then(location.reload())
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
@media (max-width: 500px) {
  .mainlogo{
    max-width: 100px!important;
  }
  .app-bar{
    max-width: 500px;
  }
  .sol{
    display: none;
  }
}
</style>
