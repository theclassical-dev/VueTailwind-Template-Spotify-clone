<template>
    <div class="bg-dark h-screen">
      <div class="flex" style="height: 88vh;">
          <!-- side navebar -->
          <div class="w-56 bg-black h-full flex-none">
              <div class="p-6">
                  <img src="01.png" alt="" class="h-10" style="">
              </div>
              <div class="mx-2 mb-5">
                  <button :key="page.id" v-for="page in sideBtn" @click="setID = page.id" :class="`w-full focus:outline-none text-sm font-semibold rounded px-3 py-2 flex items-center justify-start ${setID === page.id ? 'bg-light text-white' :'text-lightest'}`">
                      <i class="material-icons mr-3"> {{page.icon}}</i>
                      <p>{{ page.name }}</p>
                  </button>
              </div>
              <div class="mx-5">
                  <h1 class="mb-3 text-xs text-lightest tracking-widest uppercase">Playlists</h1>
                  <button class="flex items-center justify-start opacity-75 hover:opacity-100 mb-2">
                      <img src="02.png" class="h-8 w-8 mr-3"/>
                      <p class="text-sm text-white font-semibold">Create Playlist</p>
                  </button>
                  <button class="flex items-center justify-start opacity-75 hover:opacity-100">
                      <img src="03.png" class="h-8 w-8 mr-3"/>
                      <p class="text-sm text-white font-semibold">Liked Songs</p>
                  </button>
                  <div class="h-px w-full bg-light my-3"></div>
              </div>
              <div class="mx-5">
                  <div class="w-full h-12 overflow-y-scroll">
                      <p :key="album" v-for="album in albums" class="text-lightest hover:text-white text-sm py-1 font-semibold">{{ album.name }}</p>
                  </div>
                  <button class="flex items-center justify-start text-lightest hover:text-white py-2">
                      <i class="material-icons mr-3 rounded-full border text-sm border-lightest">arrow_downward</i>
                      <p class="text-sm font-semibold">Install App</p>
                  </button>
              </div>
              <div class="relative pt-4">
                  <div class="w-full h-full flex justify-end items-start opacity-0 hover:opacity-100 p-2 absolute">
                      <div class="bg-black rounded-full h-6 w-6">
                          <i class="material-icons text-white">keyboard_arrow_down</i>
                      </div>
                  </div>
                  <img src="04.jpeg" alt="">
              </div>
          </div>
          <!-- main content -->
          <div class="w-full h-full bg-yellow-100 relative">
              <!-- header -->
              <div class="w-full sticky top-0 bg-red-400 py-4 px-6 flex items-center justify-between">
                    <div class="flex items-center">
                        <button class="rounded-full bg-black w-8 h-8 mr-3 text-white">
                            <i class="material-icons text-3xl">keyboard_arrow_left</i>
                        </button>
                        <button class="rounded-full bg-black w-8 h-8 text-white">
                            <i class="material-icons text-3xl">keyboard_arrow_right</i>
                        </button>
                    </div>

                    <!-- dropdown -->
                    <div class="relative">
                        <button @click="Dropdown = true" class="focus:outline-none bg-light rounded-full py-1 px-2 flex items-center">
                            <img src="04.jpeg" class="rounded-full h-6 w-6 mr-2" alt="" />
                            <p class="text-white font-semibold text-xs mr-3">Papy Sli</p>
                            <i v-if="Dropdown === false" class="material-icons text-white">arrow_drop_down</i>
                            <i v-if="Dropdown === true" class="material-icons text-white">arrow_drop_up</i>
                        </button>
                        <div v-if="Dropdown === true" class="absolute bg-light w-full rounded mt-1">
                            <button @click="Dropdown = false" class="focus:outline-none w-full text-sm py-2 text-lightest hover:text-white border-b border-lightest opacity-75 hover:opacity-100">Acount</button>
                            <button @click="Dropdown = false" class="focus:outline-none w-full text-sm py-2 text-lightest hover:text-white border-b border-lightest opacity-75 hover:opacity-100">Logout</button>
                        </div>
                    </div>
              </div>
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
        setID: 'home',
        albums: [
            {name: 'Hello'},
            {name: 'say something'},
            {name: 'You are the reason'},
            {name: 'Someone i loved'},
            {name: 'Tomorrow'},
        ],
        Dropdown: false
    };
  },
  methods:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
