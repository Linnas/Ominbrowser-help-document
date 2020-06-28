<template>
  <div>
    <v-img src="static/img/bg.png" style="position: fixed;z-index: 999">
    </v-img>
    <v-container style="padding-top: 10%">
      <v-row>
        <v-col cols="3" v-if="!$vuetify.breakpoint.mobile">
          <v-list style="position: fixed;">
            <v-list-group
              v-for="item in items"
              :key="item.title"
              no-action
            >
              <template v-slot:activator>
                <v-list-item-content>
                  <v-list-item-title v-text="item.title"></v-list-item-title>
                </v-list-item-content>
              </template>

              <v-list-item
                v-for="subItem in item.items"
                :key="subItem.fabsc"
                @click="$vuetify.goTo(subItem.href, {offset:152})"
              >
                <v-list-item-content>
                  <v-list-item-title  v-text="subItem.fabsc"></v-list-item-title>
                </v-list-item-content>
              </v-list-item>
            </v-list-group>
          </v-list>
        </v-col>
        <v-col cols="8" class="pt-12">
          <div v-for="(section, i) in sections" :id="`pic_${i}`" :key="section.img">
            <div v-if="titles.includes(i)" class="display-1 font-weight-bold mb-4">{{items[titles.indexOf(i)].title}}</div>
            <div class="title">{{ section.subtitle }}</div>
            <v-img  
              :src="`static/pic/${section.img}`" 
              width=1050 
              aspect-ratio="1.87" 
              class="my-4" 
              contain>
            </v-img>
            <div class="pic_legend font-weight-bold">{{ section.pic_legend }}</div>
            <ol>
              <li
                v-for="(annotation, idx) in section.pic_annotation" 
                :key="`annotation_${i}_${idx}`">
                {{ annotation }}
              </li>
            </ol>
            <v-divider class="my-8"></v-divider>
          </div>
        </v-col>
        <v-col cols="1" v-if="!$vuetify.breakpoint.mobile">
          <v-fab-transition>
            <v-btn
              v-show="!hidden"
              @click="$vuetify.goTo(target, options)"
              color="green"
              dark
              fixed
              bottom
              right
              fab
            >
              <v-icon>mdi-chevron-up</v-icon>
            </v-btn>
          </v-fab-transition>
          <!-- <button @click="$vuetify.goTo(target, options)" type="button" aria-label="Scroll to top" title="Scroll to top" class="v-btn v-btn--bottom v-btn--contained v-btn--fab v-btn--fixed v-btn--right v-btn--round theme--dark v-size--large green" style="transform-origin: center center;"><span class="v-btn__content"><i aria-hidden="true" class="v-icon notranslate mdi mdi-chevron-up theme--dark" ></i></span></button> -->
        </v-col>
      </v-row>
  </v-container>
  </div>
  
</template>

<script>
import sections from '../../sections.json'
export default {
  name: 'help',
   data: () => ({
      target:0,
      hidden:false,
      homepage: 'http://omnibrowser.abiosciences.com',
      options: {
          duration: 300,
          offset: 20,
          easing: 'easeInOutCubic',
        },
      sections,
      titles:[0, 5, 6, 13, 16, 21, 22, 26, 27],
      items:[
      {
        title: 'Search',
        items: [{fabsc: 'Search Studies', href: '#pic_0'}, {fabsc: 'Search Genes', href: '#pic_2'}, {fabsc: 'Cell Ontology', href: '#pic_3'}, {fabsc: 'Integrated Dataset', href: '#pic_4'}]
      }, 
      {
        title: 'Load Dataset',
        items: [{fabsc: 'Dataset Abstract', href: '#pic_5'}]
      }, 
      {
        title: 'Dimensional Reduction',
        items: [{fabsc: 'Embedding Plot', href: '#pic_6'}, {fabsc: 'Gene Expression', href: '#pic_11'}, {fabsc: 'PAGA', href: '#pic_12'}]
      }, 
      {
        title: 'Differential Expression',
        items: [{fabsc: 'Box Plot', href: '#pic_13'}, {fabsc: 'Violin Plot', href: '#pic_14'}, {fabsc: 'Heatmap Plot', href: '#pic_15'}]
      }, 
      {
        title: 'Correlation',
        items: [{fabsc: 'Normal Plot', href: '#pic_16'}, {fabsc: 'Density Plot', href: '#pic_18'}, {fabsc: 'Similar Gene', href: '#pic_19'}, {fabsc: 'Heatmap', href: '#pic_20'}]
      }, 
      {
        title: 'Marker Genes',
        items: [{fabsc: 'Marker Info', href: '#pic_21'}]
      }, 
      {
        title: 'Supervised Annotation',
        items: [{fabsc: 'Annotation Statistics', href: '#pic_22'}, {fabsc: 'Sankey Diagram', href: '#pic_23'}, {fabsc: 'Classification Plot', href: '#pic_24'}, {fabsc: 'Classification Probatility', href: '#pic_25'}]
      }, 
      {
        title: 'Metadata',
        items: [{fabsc: 'Cell metadata analysis', href: '#pic_26'}]
      }, 
      {
        title: 'Geneset Analysis',
        items: [{fabsc: 'GO enrichment analysis', href: '#pic_27'}]
      }]
    }),
  mounted() {
    console.log(this.$vuetify.breakpoint)
    console.log(this.sections);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
html {
  scroll-padding-top: 30px; /* height of sticky header */
}
</style>
