<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <div class="bg-light-blue-7 text-white">
        <q-toolbar>
          <q-btn
            flat
            round
            dense
            icon="menu"
            aria-label="Menu"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-space />
        </q-toolbar>
        <q-toolbar inset>
          <q-toolbar-title>
              Cotação de moedas
            </q-toolbar-title>
        </q-toolbar>
      </div>
    </q-header>
     <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="200"
        :breakpoint="400">
        <q-scroll-area style="height: calc(100% - 150px); margin-top: 150px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="ion-logo-github" />
              </q-item-section>

              <q-item-section @click="sendToGitHub()">
                Github
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="ion-logo-linkedin" />
              </q-item-section>
              <q-item-section @click="sentToLinkedIn()">
                LinkedIn
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="https://cdn.quasar.dev/img/material.png" style="height: 150px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="https://media-exp1.licdn.com/dms/image/C4E03AQF7afmiM9TRUg/profile-displayphoto-shrink_200_200/0?e=1590624000&v=beta&t=E96w4c15AzPX4Q2d-WoBeo0Hs4n31O8sQfMvaYp61xs">
            </q-avatar>
            <div class="text-weight-bold">Douglas Henrique</div>
            <div>Full Stack Developer</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>

export default {
  name: 'MainLayout',

  data () {
    return {
      leftDrawerOpen: false,
    }
  },
  created () {
    this.$q.addressbarColor.set('#a2e3fa')
  },
  methods: {
    sendToGitHub : function () {
      location.replace("https://github.com/douglas-henrique/coin-watcher");
    },
    sentToLinkedIn : function () {
      location.replace("https://linkedin.com/in/douglas-hsp");
    }
  }
}
</script>
