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
          <div class="w-full h-full bg-yellow-100 overflow-y-scroll relative">
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
              <!-- cards -->
                <div class="px-6 py-3">
                    <div class="flex items-center justify-between">
                        <h1 class="pl-2 text-2xl font-semibold text-white tracking-wider hover:underline">Recently Played</h1>
                        <h2 class="pr-8 pt-4 text-xs font-semibold text-lightest tracking-wider uppercase hover:underline mb-3">See All</h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <div :key="recent" v-for="recent in recents" class="p-2 w-48 flex flex-1 relative">
                            <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                                <div class="bg-green rounded-full w-10 h-10 flex items-center justify-center">
                                    <i class="material-icons text-white text-2xl">play_arrow</i>
                                </div>
                            </div>
                            <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                                <img :src="`${ recent.src}`" alt="" class="h-auto w-full shadow mb-2">
                                <h1 class="text-sm font-semibold text-white tracking wide">{{ recent.title }}</h1>
                                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ recent.artist }}</h2>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- second card -->
                <div class="px-6 py-3">
                    <div class="pl-2">
                        <h1 class="text-2xl font-semibold text-white tracking-wider hover:underline">Made for Clasic Sli</h1>
                        <h2 class="text-sm text-lightest mb-2">Get better recommendations the more you listen.</h2>
                    </div>
                    <div class="w-full flex flex-wrap">
                        <div :key="custom" v-for="custom in customs" class="p-2 w-48 flex flex-1 relative">
                            <div class="absolute w-full h-full flex items-end justify-end p-8 opacity-0 hover:opacity-100">
                                <div class="bg-green rounded-full w-10 h-10 flex items-center justify-center">
                                    <i class="material-icons text-white text-2xl">play_arrow</i>
                                </div>
                            </div>
                            <div class="bg-light w-full h-auto p-5 rounded-lg shadow-md">
                                <img :src="`${ custom.src}`" alt="" class="h-auto w-full shadow mb-2">
                                <h1 class="text-sm font-semibold text-white tracking wide">{{ custom.title }}</h1>
                                <h2 class="text-xs text-lightest tracking-wide pb-5">{{ custom.artist }}</h2>
                            </div>
                        </div>
                    </div>
                </div>
          </div>
      </div>
      <!-- play bar -->
      <div class="w-full flex items-center justify-between px-3 bg-light" style="height: 12vh; ">
          <div class="flex items-center">
              <div>
                <h1 class="text-sm text-white tracking-wide">Bady Riddem - Five</h1>
                <h2 class="text-xm text-lightest tracking-wide">Baby's Riddim</h2>
              </div>
              <i class="material-icons text-xl text-green mx-4"> favorite</i>
              <i class="material-icons text-xl text-lightest">picture_in_picture</i>
          </div>
          <div class="flex items-center">
              <i class="material-icons text-lightest">playlist_play</i>
              <i class="material-icons text-xl text-lightest mx-3">important_devices</i>
              <i class="material-icons text-xl text-lightest">volume_up</i>
              <div class="w-20 ml-1 bg-lightest rounded-full h-1"></div>
          </div>
      </div>
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
        Dropdown: false,
        recents: [
            {src: '04.jpeg', title: 'Capi Dem', artist: 'Olamide'},
            {src: '5.jpg', title: 'Made in Lagos', artist: 'Wizkid'},
            {src: '04.jpeg', title: 'Capi Dem', artist: 'Olamide'},
            {src: '04.jpeg', title: 'Twince as Tall', artist: 'Burna Boy'},
            {src: '5.jpg', title: 'Smile', artist: 'Wizkid'},
            {src: '04.jpeg', title: 'Capi Dem', artist: 'Olamide'},
        ],
        customs: [
            {src: '04.jpeg', title: 'Mix Capi Dem', artist: 'Olamide'},
            {src: '5.jpg', title: 'Made in Lagos', artist: 'Wizkid'},
            {src: '07.png', title: 'Capi Dem', artist: 'Olamide'},
            {src: '09.png', title: 'Twince as Tall', artist: 'Burna Boy'},
            {src: '04.jpeg', title: 'Capi Dem', artist: 'Olamide'},
            {src: '04.jpeg', title: 'Capi Dem', artist: 'Olamide'},
        ],
    };
  },
  methods:{

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
