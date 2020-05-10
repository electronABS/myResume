<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'Work experience' : 'My Life in a Nutshell'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Summary' : 'Detailed'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        year : 'JUN 2014 JUIL 2014',
        title: 'Trainee',
        html : ``,
        iconImage: 'img/timeline/ommp-logo.png',
      },
      {
        year : 'FEV 2016 JUN 2016',
        title: 'Trainee',
        html : ``,
        iconImage: 'img/timeline/ommp-logo.png',
      },
      {
        year : 'JUN 2017 SEP 2017',
        title: 'Trainee',
        html : ``,
        iconImage: 'img/timeline/uib-logo.png',
      },
      {
        year : 'AOUT 2017 SEP 2017',
        title: 'Trainee',
        html : ``,
        iconImage: 'img/timeline/ubci-logo.png',
      },
      {
        year : 'FEV 2018  JUL 2018',
        title: 'Trainee',
        html : ``,
        iconImage: 'img/timeline/digitalberry-logo.png',
      },
      {
        year : 'Now',
        title: 'Full Stack Software Engineer',
        html : `<dl>
                  <dt><h4><a target="_blank" href="https://www.digitalberry.fr/en/solution/automated-digital-certificate-management-solution/">BerryCert</a><h4></dt>
                  <ul>
                    <li><b>Current Status</b> : <span class="light-blue--text lighten-3">Deployed</span> , Team : 8</li>
                    <li><b>Description</b> : A Digital certificate lifecycle management software that can detects and automatically manages certificates' renewal before their expiration date with an ergonomoic monitoring dashboards.</li>
                    <li><b>Technologies</b> : Spring , Junit , Angular , ElasticSearch , postgreSQL , Docker , Jenkins , JIRA , SCRUM...</li>
                  </ul><br>

                  <dt><h4><a target="_blank" href="https://www.digitalberry.fr/en/solution/blockchain-solution-for-traceability-of-data-with-legal-value/">BerryCord</a><h4></dt>
                  <ul>
                    <li><b>Current Status</b> : <span class="light-blue--text lighten-3">Deployed</span> , Team : 4</li>
                    <li><b>Description</b> : </li>
                    <li><b>Technologies</b> : Hyperledger Fabric/Explorer , Spring , Junit , Angular , ElasticSearch , postgreSQL , Docker , Jenkins , JIRA , SCRUM...</li>
                  </ul><br>

                  <dt><h4>Microsoft Public Key Infrastructure<h4></dt>
                  <ul>
                    <li><b>Current Status</b> : <span class="light-blue--text lighten-3">On production</span> , Team : 4</li>
                    <li><b>Description</b> : Setup and delivery a microsoft public key infrastructure.</li>
                    <li><b>Technologies</b> : Windows server 2012 R2 : (ADCS / ADDS / Failover clustering) , powershell</li>
                  </ul>
                </dl>`,
        image: 'img/timeline/berrycert_dashboard.png',
        iconImage: 'img/timeline/digitalberry-logo.png',
      },
      
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
