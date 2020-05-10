<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        title="Who am I?"
      >
        I'm a developer born in Tunisia and softaware engineer at <a href="https://www.digitalberry.fr/">Digitalberry.fr</a>.
        I'm interested and skilled in different topics of Information Technology including programming, web development, and security.
        Extremely motivated to develop constantly my skills and grow professionally. I am confident in my ability to speak the machine langage.
      </content-section>
      <content-section
        v-if="prouds"
        title="What am I proud of?"
      >
        <v-layout
          v-for="(proud, i) in prouds"
          :key="i"
        >
          <v-flex
            md1
            xs3
          >
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex
            md11
            xs9
          >
            <p>
              <strong>{{ proud.text }}</strong><br>
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="educations"
        title="Education"
      >
        <v-layout
          v-for="(education, i) in educations"
          :key="i"
        >
          <v-flex md4>
            {{ education.from }} - {{ education.to }}
          </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <i>{{ education.location }}</i>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section
        v-if="skills"
        id="to-timeline"
        title="Skills"
      >
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template
            v-for="(skill, i) in skills"
          >
            <v-flex
              v-if="skill.divider"
              :key="i"
              md12
              xs12
              mb-4
            />
            <v-flex
              v-else
              :key="i"
              md6
              xs12
            >
              <div
                class="mr-2 ml-2"
              >
                <div class="align-center">
                  <v-icon
                    small
                  >
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'MainContent',
  components: { ContentSection },
  data      : () => ({
    prouds: [
      {
        icon  : 'mdi-help-rhombus-outline',
        text  : 'Answered 10M+ questions!',
        source: '(Bytegate.ir post views)',
      },
      {
        icon  : 'mdi-library-music',
        text  : 'Made people enjoy and learn a new language for equivalent of 29+ years (older than myself!)',
        source: '(Bobet.ir and its channel downloads)',
      },
      {
        icon  : 'mdi-timer-sand',
        text  : 'Saved +110 days of time of students, writers and etc!',
        source: '(Delix.ir service usages)',
      },
      {
        icon  : 'mdi-account-multiple',
        text  : 'Tried to cover small part of 7 people expenses.',
        source: '(My awesome colleagues)',
      },
    ],
    educations: [
      {
        from       : '2017',
        to         : '2019',
        title      : 'Master\'s degree, Information Systems Security',
        location   : 'High Institute of management of Tunis, Tunisia',
        description: 'High honorous',
      },
      {
        from       : '2014',
        to         : '2017',
        title      : 'Bachelor\'s degree, Computer science applied to management',
        location   : 'High Institute of management of Tunis, Tunisia',
        description: 'Mention well',
      },
      {
        from       : '2013',
        to         : '2014',
        title      : 'Baccalaureate\'s degree, Mathematics',
        location   : 'Ibnou Rachik high school',
        description: 'Mention well',
      },
    ],
    skills: [
      {
        title: 'Java (Spring Framework)',
        icon : 'mdi-language-java',
        value: 80,
      },
      {
        title: 'Python (Django Framework)',
        icon : 'mdi-language-python',
        value: 40,
      },
      {
        title: 'Angular',
        icon : 'mdi-angular',
        value: 60,
      },
      {
        title: 'Vue.js Framework',
        icon : 'mdi-vuejs',
        value: 50,
      },
      { divider: true },
      {
        title: 'Ubuntu Server',
        icon : 'mdi-ubuntu',
        value: 60,
      },
      {
        title: 'Windows Server',
        icon : 'mdi-windows',
        value: 47,
      },
      {
        title: 'Kali',
        icon : 'mdi-security',
        value: 47,
      },
      {
        title: 'Web Application Security',
        icon : 'mdi-shield-lock',
        value: 80,
      },
      {divider : true},
      {
        title: 'Test Driven Development',
        icon : 'mdi-test-tube',
        value: 45,
      },
      {
        title: 'CI/CD',
        icon : 'mdi-truck-fast',
        value: 70,
      },
      {
        title: 'Git',
        icon : 'mdi-git',
        value: 67,
      },
      {
        title: 'Docker',
        icon : 'mdi-docker',
        value: 67,
      },
      { divider: true },
      {
        title: 'Team spirit',
        icon : 'mdi-account-group',
        value: 70,
      },
      {
        title: 'Scrum',
        icon : 'mdi-puzzle',
        value: 70,
      }
    ],
  }),
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
