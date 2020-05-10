<template>
  <v-card
    color="grey darken-3"
    dark
  >
    <v-card-text>
      <avatar />
      <div class="text-sm-center mb-4 mt-3">
        <h1>
          Ahmed <span class="light-blue--text text--lighten-3">Ben Salah</span>
        </h1>
        <span>
          Full Stack Software Engineer
        </span>
      </div>

      <sidebar-section :options="sections.info" />
      <sidebar-section :options="sections.socials" />
      <sidebar-section :options="sections.hobbies">
        <template v-slot:item="{item}">
          <v-chip>
            <v-avatar>
              <v-icon>
                {{ item.icon }}
              </v-icon>
            </v-avatar>
            {{ item.text }}
          </v-chip>
        </template>
      </sidebar-section>
      <sidebar-section :options="sections.languages">
        <template v-slot:items="{items}">
          <v-container pa-0>
            <v-layout
              wrap
              class="text-xs-center"
            >
              <template
                v-for="(item, i) in items"
              >
                <v-flex
                  :key="i"
                  md3
                  sm4
                  xs6
                >
                  <v-progress-circular
                    rotate="360"
                    size="65"
                    width="2"
                    :value="item.value"
                    color="white"
                    class="ma-2"
                  >
                    {{ item.text }}
                  </v-progress-circular>
                </v-flex>
              </template>
            </v-layout>
          </v-container>
        </template>
      </sidebar-section>
    </v-card-text>
  </v-card>
</template>

<script>
import Avatar from '@/views/dark-template/sidebar/Avatar'
import SidebarSection from '@/views/dark-template/sidebar/Section'
export default {
  name      : 'Sidebar',
  components: { SidebarSection, Avatar },
  data () {
    return {
      sections: {
        info: {
          title: 'INFO',
          items: [
            {
              name: 'Email',
              icon: 'mdi-email',
              text: 'ahmed_ben_salah_pc@outlook.fr',
            },
            {
              name: 'Website',
              icon: 'mdi-web',
              text: 'ahmedbensalah.in',
            },
            {
              name: 'Birth Date',
              icon: 'mdi-cake-variant',
              text: 'Mai 20, 1994',
            },
            {
              name: 'Habitation',
              icon: 'mdi-map-marker',
              text: 'Tunis, Tunisia',
            },
          ],
        },
        socials: {
          title: 'SOCIALS',
          items: [
            {
              icon: 'mdi-github-circle',
              text: 'github.com/electronABS',
              link: 'https://github.com/electronABS',
            },
            {
              icon: 'mdi-linkedin-box',
              text: 'linkedin.com/in/ahmed-ben-salah',
              link: 'https://www.linkedin.com/in/ahmed-ben-salah-5a7a2584/',
            },
            {
              icon: 'mdi-facebook-box',
              text: 'facebook.com/ahmed.bensalah',
              link: 'https://www.facebook.com/ahmed.bensalah.35',
            },
            {
              icon: 'mdi-instagram',
              text: 'instagram.com/abselectron/',
              link: 'https://www.instagram.com/abselectron/',
            },
          ],
        },
        hobbies: {
          title: 'HOBBIES',
          items: [

            {
              icon: 'mdi-run',
              text: 'Jogging',
            },
            // {
            //   icon: 'mdi-biohazard',
            //   text: 'Challenges',
            // },
            // {
            //   icon: 'mdi-bike',
            //   text: 'Cycling',
            // },
            {
              icon: 'mdi-image-filter-hdr',
              text: 'Nature',
            },
            // {
            //   icon: 'mdi-auto-fix',
            //   text: 'Hacking Stuffs',
            // },
            {
              icon: 'mdi-teach',
              text: 'Teaching',
            },
            // {
            //   icon: 'mdi-karate',
            //   text: 'Sports',
            // },
            {
              icon: 'mdi-music',
              text: 'Music',
            },
            // {
            //   icon: 'mdi-account-group',
            //   text: 'Leadership',
            // },
            {
              icon: 'mdi-book-open-page-variant',
              text: 'Books',
            },
            // {
            //   icon: 'mdi-android-debug-bridge',
            //   text: 'Tickling Bugs!',
            // },
            {
              icon: 'mdi-airplane',
              text: 'Traveling',
            },
          ],
        },
        languages: {
          title: 'LANGUAGES',
          items: [
            {
              text : 'English',
              value: 60,
            },
            {
              text : 'Arabic',
              value: 100,
            },
            {
              text : 'Frensh',
              value: 80,
            },
            // {
            //   text : 'Persian',
            //   value: 100,
            // },
          ],
        },
      },
    }
  },
}
</script>

<style scoped>
.sidebar{
    background: #2e2e2e;
}
</style>
