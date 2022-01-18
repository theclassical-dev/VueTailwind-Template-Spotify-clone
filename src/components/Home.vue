<template>
    <div class="bg-dark h-screen">
      <div class="flex" style="height: 88vh;">
          <!-- side navebar -->
          <div class="w-56 bg-black h-full flex-none">
              <div class="p-6">
                  <img src="01.png" alt="" class="h-10" style="">
              </div>
              <div class="mx-2">
                  <button :key="page.id" v-for="page in sideBtn" @click="setID = page.id" :class="`w-full font-xs rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' :'text-lightest'}`">
                      <i class="material-icons"> {{page.icon}}</i>
                      <p>{{ page.name }}</p>
                  </button>
              </div>
          </div>
          <!-- main content -->
          <div class="w-full h-full bg-yellow-100 relative">
              <!-- header -->
              <div class="w-full sticky top-o bg-red-400 p-2"></div>
          </div>
      </div>
      <!-- play bar -->
      <div class="w-full bg-light" style="height: 12vh; "></div>
    </div>
</template>

<script>
export default {
  name: "Home",
  props: {
    msg: String
  },
  data() {
    return {
        sideBtn: [
            {id: 'home', name: 'Home', icon: 'home'},
            {id: 'search', name: 'Search', icon: 'search'},
            {id: 'library', name: 'Your Library', icon: 'bar_chart'},
        ],
        setID: 'home'
    };
  },
  methods:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
