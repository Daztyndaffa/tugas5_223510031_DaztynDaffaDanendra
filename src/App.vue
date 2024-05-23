<template>
  <q-layout view="hHh lpR fFf" class="black-bg">
    <!-- Header -->
    <q-header bordered class="bg-black text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-icon name="sports_esports" size="md" class="q-mr-sm" />
          Mythic Games
        </q-toolbar-title>

        <q-input 
          outlined
          rounded
          dense
          placeholder="Search store"
          class="q-ml-md q-mr-md"
          v-model="searchQuery"
        >
          <template v-slot:append>
            <q-icon name="search"/>
          </template>
        </q-input>

        <q-item clickable v-ripple class="q-ml-sm">
          <q-item-section avatar>
            <q-icon name="explore" />
          </q-item-section>
          <q-item-section>
            Discover
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple class="q-ml-sm">
          <q-item-section avatar>
            <q-icon name="browse_gallery" />
          </q-item-section>
          <q-item-section>
            Browse
          </q-item-section>
        </q-item>
        <q-item clickable v-ripple class="q-ml-sm">
          <q-item-section avatar>
            <q-icon name="newspaper" />
          </q-item-section>
          <q-item-section>
            News
          </q-item-section>
        </q-item>

        <q-space />

        <q-btn dense flat round icon="favorite" class="q-ml-sm" @click="viewWishlist" />
        <q-btn dense flat round icon="shopping_cart" class="q-ml-sm" @click="viewCart" />
        <q-btn dense flat round icon="group" class="q-ml-sm" @click="viewGroup" />
        <q-btn dense flat round icon="person" @click="viewProfile" />
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" behavior="desktop" class="black-bg">
      <q-list>
        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="store" />
          </q-item-section>
          <q-item-section>
            Store
          </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="library_books" />
          </q-item-section>
          <q-item-section>
            Library
          </q-item-section>
        </q-item>

        <q-item clickable v-ripple>
          <q-item-section avatar>
            <q-icon name="settings" />
          </q-item-section>
          <q-item-section>
            Settings
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <div class="q-pa-md">
        <q-carousel
          swipeable
          animated
          v-model="slide"
          thumbnails
          infinite
        >
          <q-carousel-slide :name="1" img-src="./assets/foto/ghost.png" />
          <q-carousel-slide :name="2" img-src="./assets/foto/fc24.jpg" />
          <q-carousel-slide :name="3" img-src="./assets/foto/valorant.jpg" />
          <q-carousel-slide :name="4" img-src="./assets/foto/rdr2.jpg" />
        </q-carousel>
      </div>

      <div class="q-pa-md">
        <h5>MEGA Sale Spotlight</h5>
        <div class="row justify-around">
          <div class="col-2">
            <q-card class="my-card">
              <q-img src="./assets/foto/rdrii.jpg">
                <div class="absolute-bottom">
                  <div class="text-h6">Red Dead Redemtion II</div>
                  <div class="text-subtitle2">IDR 256,000</div>
                </div>
              </q-img>
              <q-card-actions>
                <q-btn flat>Buy</q-btn>
                <q-btn flat>More info</q-btn>
              </q-card-actions>
            </q-card>
          </div>
          <div class="col-2">
            <q-card class="my-card">
              <q-img src="./assets/foto/gta5.png">
                <div class="absolute-bottom">
                  <div class="text-h6">Grand Theft Auto V</div>
                  <div class="text-subtitle2">IDR 150,275</div>
                </div>
              </q-img>
              <q-card-actions>
                <q-btn flat>Buy</q-btn>
                <q-btn flat>More info</q-btn>
              </q-card-actions>
            </q-card>
          </div>
          <div class="col-2">
            <q-card class="my-card">
              <q-img src="./assets/foto/hogwarts.jpg">
                <div class="absolute-bottom">
                  <div class="text-h6">Hogwarts Legacy</div>
                  <div class="text-subtitle2">IDR 399,500</div>
                </div>
              </q-img>
              <q-card-actions>
                <q-btn flat>Buy</q-btn>
                <q-btn flat>More info</q-btn>
              </q-card-actions>
            </q-card>
          </div>
          <div class="col-2">
            <q-card class="my-card">
              <q-img src="./assets/foto/dead.jpg">
                <div class="absolute-bottom">
                  <div class="text-h6">Dead Island 2</div>
                  <div class="text-subtitle2">IDR 320,500</div>
                </div>
              </q-img>
              <q-card-actions>
                <q-btn flat>Buy</q-btn>
                <q-btn flat>More info</q-btn>
              </q-card-actions>
            </q-card>
          </div>
          <div class="col-2">
            <q-card class="my-card">
              <q-img src="./assets/foto/cyberpunk.jpg">
                <div class="absolute-bottom">
                  <div class="text-h6">Cyberpunk 2077: Ultimate Edition</div>
                  <div class="text-subtitle2">IDR 625,799</div>
                </div>
              </q-img>
              <q-card-actions>
                <q-btn flat>Buy</q-btn>
                <q-btn flat>More info</q-btn>
              </q-card-actions>
            </q-card>
          </div>
        </div>
      </div>

      <div class="q-pa-md" style="background-color: #F7F7F8; margin-top: 20px;">
        <div class="row justify-between items-center">
          <div class="col-auto">
            <q-icon name="card_giftcard" size="md" class="q-mr-sm" />
            <h5 class="inline-block">Free Games</h5>
          </div>
          <q-btn flat class="col-auto q-mr-md" label="View More" @click="viewMoreFreeGames"/>
        </div>
        <div class="row justify-around q-mt-md">
          <div class="col-5">
            <q-card class="my-card clickable-card" @click="viewFreeGameDetails('game1')">
              <q-img src="./assets/foto/dragon.jpg">
                <div class="absolute-bottom text-white q-pa-sm">
                  <div class="text-h6">Dragon Age: Inquisition</div>
                  <div class="text-subtitle2">Promo from May 1 to May 31</div>
                </div>
              </q-img>
            </q-card>
          </div>
          <div class="col-5">
            <q-card class="my-card clickable-card" @click="viewFreeGameDetails('game2')">
              <q-img src="./assets/foto/fortnite.jpg">
                <div class="absolute-bottom text-white q-pa-sm">
                  <div class="text-h6">Fortnite</div>
                  <div class="text-subtitle2">Promo from June 1 to June 30</div>
                </div>
              </q-img>
            </q-card>
          </div>
        </div>
      </div>

      <div class="q-pa-md" style="background-color: #F7F7F8;">
        <div class="row">
          <div class="col-4">
            <div class="row justify-between items-center">
              <div class="col-auto">
                <h5 class="inline-block">Top Seller</h5>
              </div>
              <q-btn flat class="col-auto q-mr-md" label="View More" @click="viewMoreTopSeller"/>
            </div>
            <q-list bordered>
              <q-item clickable v-ripple v-for="item in topSeller" :key="item.id" @click="viewGameDetails(item.id)">
                <q-item-section avatar>
                  <q-img :src="item.image" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>{{ item.title }}</q-item-label>
                  <q-item-label caption>{{ item.price }}</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </div>

          <div class="col-4">
            <div class="row justify-between items-center">
              <div class="col-auto">
                <h5 class="inline-block">Most Played</h5>
              </div>
              <q-btn flat class="col-auto q-mr-md" label="View More" @click="viewMoreMostPlayed"/>
            </div>
            <q-list bordered>
              <q-item clickable v-ripple v-for="item in mostPlayed" :key="item.id" @click="viewGameDetails(item.id)">
                <q-item-section avatar>
                  <q-img :src="item.image" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>{{ item.title }}</q-item-label>
                  <q-item-label caption>{{ item.price }}</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </div>

          <div class="col-4">
            <div class="row justify-between items-center">
              <div class="col-auto">
                <h5 class="inline-block">Top Upcoming Wishlisted</h5>
              </div>
              <q-btn flat class="col-auto q-mr-md" label="View More" @click="viewMoreTopUpcomingWishlisted"/>
            </div>
            <q-list bordered>
              <q-item clickable v-ripple v-for="item in topUpcomingWishlisted" :key="item.id" @click="viewGameDetails(item.id)">
                <q-item-section avatar>
                  <q-img :src="item.image" />
                </q-item-section>
                <q-item-section>
                  <q-item-label>{{ item.title }}</q-item-label>
                  <q-item-label caption>{{ item.price }}</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </div>
        </div>
      </div>
      
      <router-view />
    </q-page-container>

    <q-footer bordered class="bg-black text-white footer-centered">
      <q-toolbar>
        <q-toolbar-title>
          <q-icon name="sports_esports" size="md" class="q-mr-sm" />
          <div>Mythic Games</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
    const leftDrawerOpen = ref(false)
    const searchQuery = ref('')

    const topSeller = ref([
      { id: '1', image: 'https://cdn1.epicgames.com/offer/4750c68b2bfa4f43933b81cfd5cc510c/EGS_EASPORTSFC24StandardEdition_EACanada_S2_1200x1600-37aa3816ed46542836e1068060998810', title: 'EA SPORTS FC 24', price: 'IDR 151,800' },
      { id: '2', image: 'https://upload.wikimedia.org/wikipedia/en/thumb/a/a5/Grand_Theft_Auto_V.png/220px-Grand_Theft_Auto_V.png', title: 'Grand Theft Auto V', price: 'IDR 150,375' },
      { id: '3', image: 'https://cdn1.epicgames.com/epic/offer/RDR2PC1227_Epic%20Games_860x1148-860x1148-b4c2210ee0c3c3b843a8de399bfe7f5c.jpg', title: 'Red Dead Redemtion 2', price: 'IDR 256,000' },
      { id: '4', image: 'https://cdn1.epicgames.com/offer/6e6aa039c73347b885803de65ac5d3db/EGS_GhostofTsushima_SuckerPunchProductions_S2_1200x1600-e23e02c1d70be7b528dba50860f87d39', title: 'Ghost Of Tsusima', price: 'IDR 879,000' },
      { id: '5', image: 'https://cdn2.unrealengine.com/egs-deadbydaylightgoldedition-behaviourinteractive-editions-s2-1200x1600-738fb46b00fe.jpg', title: 'Dead by Daylight', price: 'IDR 67,600' },
    ])

    const mostPlayed = ref([
      { id: '1', image: 'https://static-cdn.jtvnw.net/ttv-boxart/33214-272x380.jpg', title: 'Fortnite', price: 'Free' },
      { id: '2', image: 'https://cdn1.epicgames.com/offer/9773aa1aa54f4f7b80e44bef04986cea/EGS_RocketLeagueSeason14RocketeerPack_PsyonixLLC_DLC_S2_1200x1600-22e6768ca24852707005aaddeee4d4d3?h=480&quality=medium&resize=1&w=360', title: 'Rocket League', price: 'Free' },
      { id: '3', image: 'https://cdn1.epicgames.com/offer/cbd5b3d310a54b12bf3fe8c41994174f/EGS_VALORANT_RiotGames_S2_1200x1600-780189aef89b5076cef49b93e40633a0', title: 'Valorant', price: 'Free' },
      { id: '4', image: 'https://adrare.net/wp-content/uploads/2023/12/genshin.jpg', title: 'Genshin Impact', price: 'Free' },
      { id: '5', image: 'https://cdn1.epicgames.com/offer/2a14cf8a83b149919a2399504e5686a6/EGS_TheSims4_ElectronicArts_S2_1200x1600-ceadc3bd1e6f885ad64d9f115f51f5c0', title: 'The Sims 4', price: 'Free' },
    ])

    const topUpcomingWishlisted = ref([
      { id: '1', image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQqLZCowqWgouU2oj8VzcU5dBCyszEGKRT-v1C5iaAqnD3dAuzs9-ws6P-PfZmKzFpVWEg&usqp=CAU', title: 'Black Myth: Wukong', price: 'Available 08/20/24' },
      { id: '2', image: 'https://cdn.marvel.com/content/1x/marvelrivals_lob_crd_01.jpg', title: 'Marvel Rivals', price: 'Coming sson' },
      { id: '3', image: 'https://cdn1.epicgames.com/offer/32bc7c6aaecd40eeb5f58bb83dba1c05/EGS_Frostpunk2_11bitstudios_S2_1200x1600-8b452490754cb4a4fe1a983c533cfb5d', title: 'Frostpunk 2', price: 'IDR 338,999' },
      { id: '4', image: 'https://cdn1.epicgames.com/offer/97590ba7ef144232b14093375c468032/EGS_TheWolfAmongUs2_Telltale_S2_1200x1600-28a121945b86101ea1b20cc3d5f86e78', title: 'The Wolf Among Us 2', price: 'Coming Soon' },
      { id: '5', image: 'https://cdn1.epicgames.com/offer/e860fa919120430ca12c557bb676bc6a/EGST_StorePortrait_1200x1600_1200x1600-e6f41420c20529e7380243a6f6b7a38f', title: 'Star Wars Outlaw', price: 'IDR 809,000' },
    ])

    const toggleLeftDrawer = () => {
      leftDrawerOpen.value = !leftDrawerOpen.value
    }

    const viewWishlist = () => {
      console.log('Viewing wishlist')
      // Add your wishlist viewing logic here
    }

    const viewCart = () => {
      console.log('Viewing cart')
      // Add your cart viewing logic here
    }

    const viewGroup = () => {
      console.log('Viewing group')
      // Add your group viewing logic here
    }

    const viewProfile = () => {
      console.log('Viewing profile')
      // Add your profile viewing logic here
    }

    const viewMoreFreeGames = () => {
      console.log('Viewing more free games')
      // Add your view more free games logic here
    }

    const viewFreeGameDetails = (gameId) => {
      console.log(`Viewing details for ${gameId}`)
      // Add your view free game details logic here
    }

    const viewMoreTopSeller = () => {
      console.log('Viewing more top seller games')
      // Add your view more top seller games logic here
    }

    const viewMoreMostPlayed = () => {
      console.log('Viewing more most played games')
      // Add your view more most played games logic here
    }

    const viewMoreTopUpcomingWishlisted = () => {
      console.log('Viewing more top upcoming wishlisted games')
      // Add your view more top upcoming wishlisted games logic here
    }

    const viewGameDetails = (gameId) => {
      console.log(`Viewing details for ${gameId}`)
      // Add your view game details logic here
    }

    return {
      leftDrawerOpen,
      searchQuery,
      slide: ref(1),
      toggleLeftDrawer,
      viewWishlist,
      viewCart,
      viewGroup,
      viewProfile,
      viewMoreFreeGames,
      viewFreeGameDetails,
      viewMoreTopSeller,
      viewMoreMostPlayed,
      viewMoreTopUpcomingWishlisted,
      viewGameDetails,
      topSeller,
      mostPlayed,
      topUpcomingWishlisted
    }
  }
}
</script>

<style lang="sass" scoped>
.my-card
  width: 100%

.clickable-card
  cursor: pointer

.black-bg
  background-color: #000

.footer-centered
  text-align: center

.q-drawer__content
  background-color: #000

.my-card
  background-color: #ccc
</style>
