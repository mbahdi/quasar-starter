<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo</div>
        <!-- <div class="text-h6">Darmadi</div> -->
        <div class="text-subtitle1">{{todaysDate.greeting}}</div>
        <div class="text-subtitle2">{{todaysDate.date}}</div>
      </div>
      <q-img src="statics/strawberry.jpg" class="header-image absolute-top"></q-img>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 214px); margin-top: 214px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
              to="/"
              exact
              clickable
              v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>

            <q-item to="/help" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>

            <q-item to="/login" exact clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="vpn_key" />
              </q-item-section>

              <q-item-section>
                Login
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="statics/strawberry.jpg" style="height: 214px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="70px" class="q-mb-sm">
              <img src="statics/pp.png">
            </q-avatar>
            <div class="text-weight-bold">Darmadi</div>
            <div>@mbahdi</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>

    <q-footer reveal bordered class="bg-primary text-white">
      <q-tabs
        v-model="tab"
        indicator-color="transparent"
        active-color="white"
        class="bg-primary text-red-11 shadow-2">
        <q-tab name="home" icon="home" />
        <q-tab name="help" icon="help" />
        <q-tab name="login" icon="vpn_key" />
      </q-tabs>
    </q-footer>
  </q-layout>
</template>

<script>
// import EssentialLink from 'components/EssentialLink'
import { date } from 'quasar'

export default {
  name: 'MainLayout',

  components: {
    // EssentialLink
  },

  data () {
    return {
      leftDrawerOpen: false,
      tab: 'home',
      essentialLinks: [
        {
          title: 'Docs',
          caption: 'quasar.dev',
          icon: 'school',
          link: 'https://quasar.dev'
        },
        {
          title: 'Github',
          caption: 'github.com/quasarframework',
          icon: 'code',
          link: 'https://github.com/quasarframework'
        },
        {
          title: 'Discord Chat Channel',
          caption: 'chat.quasar.dev',
          icon: 'chat',
          link: 'https://chat.quasar.dev'
        },
        {
          title: 'Forum',
          caption: 'forum.quasar.dev',
          icon: 'record_voice_over',
          link: 'https://forum.quasar.dev'
        },
        {
          title: 'Twitter',
          caption: '@quasarframework',
          icon: 'rss_feed',
          link: 'https://twitter.quasar.dev'
        },
        {
          title: 'Facebook',
          caption: '@QuasarFramework',
          icon: 'public',
          link: 'https://facebook.quasar.dev'
        },
        {
          title: 'Quasar Awesome',
          caption: 'Community Quasar projects',
          icon: 'favorite',
          link: 'https://awesome.quasar.dev'
        }
      ]
    }
  },
  computed: {
    todaysDate () {
      const timeStamp = Date.now()
      const today = new Date()
      const curHr = today.getHours()
      const myret = {}

      if (curHr < 12) {
        myret.greeting = 'Selamat Pagi'
        // console.log('good morning')
      } else if (curHr < 18) {
        myret.greeting = 'Selamat Sore'
        // console.log('good afternoon')
      } else {
        myret.greeting = 'Selamat Malam'
        // console.log('good evening')
      }
      myret.date = date.formatDate(timeStamp, 'DD MMMM, YYYY HH:mm:ss')
      return myret
    },
    currentRouteName () {
      console.log(this.$route.name)
      return this.$route.name
    }
  }
}
</script>

<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.2;
  filter: grayscale(100%);
}
</style>
