<template>
  <v-content>
    <v-img src="static/img/bg.png" align="center" style="position: fixed;z-index: 999">
      <v-img src="static/img/introduction.png" width=481 height=71 class="mt-12">
      </v-img>
    </v-img>
    <v-container>
    
    <v-row class="custom_row" style="margin-left: 100px;margin-top: 180px;">
      <v-col cols="3">
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
        <div v-for="(img, i) in imgs" :id="`pic_${i}`" :key="i">
          <div v-if="titles.includes(i)" class="display-1 font-weight-bold mb-4">{{items[titles.indexOf(i)].title}}</div>
          <div class="title">{{ subtitles[i] }}</div>
          <v-img  :src="img" width=1050 aspect-ratio="1.87" class="my-4" contain></v-img>
          <div class="pic_legend font-weight-bold">{{ pic_legends[i].pic_legend }}</div>
          <div class="pic_annotation" v-for="(annotation, idx) in pic_legends[i].pic_annotation" v-bind:key="`annotation_${idx}`">
            <div class="ml-2">0{{idx+1}}: &nbsp; {{ annotation }}</div>
          </div>
          <v-divider class="mt-8"></v-divider>
        </div>
      </v-col>
      <v-col cols="1">
        <button type="button" aria-label="Scroll to top" title="Scroll to top" class="v-btn v-btn--bottom v-btn--contained v-btn--fab v-btn--fixed v-btn--right v-btn--round theme--dark v-size--large green" style="transform-origin: center center;"><span class="v-btn__content"><i aria-hidden="true" class="v-icon notranslate mdi mdi-chevron-up theme--dark" @click="$vuetify.goTo(target, options)"></i></span></button>
      </v-col>
    </v-row>
    </v-container>
  </v-content>
</template>

<script>
export default {
  name: 'help',
   data: () => ({
      target:0,
      homepage: 'http://omnibrowser.abiosciences.com',
      options: {
          duration: 300,
          offset: 0,
          easing: 'easeInOutCubic',
        },
      titles:[0, 5, 7, 9, 12, 16, 17, 21, 22],
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
        items: [{fabsc: 'Embedding Plot', href: '#pic_6'}, {fabsc: 'Gene Expression', href: '#pic_7'}, {fabsc: 'PAGA', href: '#pic_8'}]
      }, 
      {
        title: 'Differential Expression',
        items: [{fabsc: 'Box Plot', href: '#pic_9'}, {fabsc: 'Violin Plot', href: '#pic_10'}, {fabsc: 'Heatmap Plot', href: '#pic_11'}]
      }, 
      {
        title: 'Correlation',
        items: [{fabsc: 'Normal Plot', href: '#pic_12'}, {fabsc: 'Density Plot', href: '#pic_13'}, {fabsc: 'Similar Gene', href: '#pic_14'}, {fabsc: 'Heatmap', href: '#pic_15'}]
      }, 
      {
        title: 'Marker Genes',
        items: [{fabsc: 'Marker Info', href: '#pic_16'}]
      }, 
      {
        title: 'Supervised Annotation',
        items: [{fabsc: 'Annotation Statistics', href: '#pic_17'}, {fabsc: 'Sankey Diagram', href: '#pic_18'}, {fabsc: 'Classification Plot', href: '#pic_19'}, {fabsc: 'Classification Probatility', href: '#pic_20'}]
      }, 
      {
        title: 'Metadata',
        items: [{fabsc: 'Cell metadata analysis', href: '#pic_21'}]
      }, 
      {
        title: 'Geneset Analysis',
        items: [{fabsc: 'GO enrichment analysis', href: '#pic_22'}]
      }],
      imgs:['static/pic/pic_1.png', 'static/pic/pic_2.png', 'static/pic/pic_3.png', 'static/pic/pic_4.png', 'static/pic/pic_5.png', 'static/pic/pic_6.png', 'static/pic/pic_7.png', 'static/pic/pic_8.png', 'static/pic/pic_9.png', 'static/pic/pic_10.png', 'static/pic/pic_11.png', 'static/pic/pic_12.png','static/pic/pic_13.png', 'static/pic/pic_14.png', 'static/pic/pic_15.png', 'static/pic/pic_16.png', 'static/pic/pic_17.png', 'static/pic/pic_18.png', 'static/pic/pic_19.png', 'static/pic/pic_20.png', 'static/pic/pic_21.png', 'static/pic/pic_22.png', 'static/pic/pic_23.png'],
      subtitles:['Search Studies(statistic)', 'Search Studies(list)', 'Search Genes', 'Cell Ontology', 'Integrated Dataset', 'Dataset Abstract', 'Embed Plot', 'Gene Expression', 'PAGA', 'Box Plot', 'Violin Plot', 'Heatmap Plot', 'Normal Plot', 'Density Plot', 'Similar Gene', 'Heatmap', 'Marker Info', 'Annotation Statistics', 'Sankey Diagram', 'Classification Plot', 'Classification Probatility', 'Cell metadata analysis', 'GO enrichment analysis'],
      pic_legends:[{
       pic_legend:'Statistic data can be visualized via pie chart and histogram.',
       pic_annotation:['You can hide the side navigation to icons.', 'Switch between data list and statistic graphs.', 'Publication Date is identical to the one in lists.', 'Same with lists.'],
      },{
       pic_legend:'A list of all datasets based on keywords. Each entity consists of the title, number of cells, and publication date. More detailed information is displayed as tags, which can be refined by the upper search box.',
       pic_annotation:['Filter the research field.', 'Choose the range of publication date of the article.', 'Choose the sequencing platform.', 'Choose the tissues  you interested in.', 'Choose the publication journal.'],
      },{
       pic_legend:'Each entity is supplied with the box plot to show the log2(TPM) of all clusters in this dataset.',
       pic_annotation:['Search by genes.', 'Input gene names(with auto-completion).', 'Filter by F-test', 'Sort by ascending or descending.'],
      },{
       pic_legend:'Besides gene search, you can also filter datasets by cell ontology.',
       pic_annotation:['Click cell ontology.', 'input cell names as keywords.', 'Sort by publication date or cell number.'],
      },{
       pic_legend:'12 integrated datasets are provided.',
       pic_annotation:['Click integrated datasets.', 'Keywords will be highlighted.'],
      },{
       pic_legend:'After you have clicked into an entity, an abstract outlines the background of this dataset. Similar cell ontology and gene ontology are also shown here.',
       pic_annotation:['Load the dataset you chose.', 'Article figures can be viewed via this button.', 'Look for the related publicatons by adjusting the ontology distance.'],
      },{
       pic_legend:'We provide two demsional reduction methods and genes expression visiulization.',
       pic_annotation:['Click Dimensional Reduction.', 'Both t-SNE & UMAP are available.', 'Gene expression can be searched and displayed via heatmap (log2(TPM+1)). Average expression value will be displayed for multiple genes.', 'Groupby functions. Cells can be grouped and colored according to their cell types. Other groupby choices are also available according to each dataset.', 'Cell filtering. Display only cell groups of interest.', ],
      },{
       pic_legend:'Genes expression level over all clusters',
       pic_annotation:['All the selected genes are compared with each other via gene expression graphs.', 'Average expression level on the whole graph.'],
      },{
       pic_legend:'PAGA graph shows the conncetivity within clusters, each node represents a cell group, differentiated by their color, with node size indicating cell number, the width of edges reflects similarity between conncected cell groups.',
       pic_annotation:['Show PAGA graph.', 'Gene expression query can be performed similarly to the t-SNE plot.', 'Each cluster is sorted descendingly by cell number.', 'Similarity threshold: Only display edges above a certain threshold to reflect major trajectories.'],
      },{
       pic_legend:'Box plot and violin plot reflect the differential expression of genes across different cell groups. A real-time F-test is applied to evaluate significance, with p values marked on the plot title.',
       pic_annotation:['Click differential expression.', 'Different plot methods can be switched via tabs. ', 'Cell types & other cell annotations can be used to group the data.', 'Whether or not the scatter plot will be shown on the box plot', 'Gene expression query can be performed similarly, with average expression value returned for multiple inputs.'],
      },{
       pic_legend:'Box plot and violin plot to relect differential expression of genes across different cell groups. A real-time F-test is adopted to evaluate significance, with p values marked on the plot title.',
       pic_annotation:['Gene expression query can be performed similarly, with averaged expression value returned for multiple inputs.', 'Cell types & other cell annotations can be used to group the data.'],
      },{
       pic_legend:'Gene-cluster heatmap displays gene expression patterns between clusters. Each unit of matrix represents average gene expression within the cell group.',
       pic_annotation:['Click heatmap plot', 'Gene set query.'],
      },{
       pic_legend:'2D scatter plot, with each point representing a single cell and axis representing two genes. Pearson correlation efficiency is displayed in the title',
       pic_annotation:['Click correlation', 'Choose plot type', 'Input signature A', 'Tabs can be used to switch between correlation, similar genes and correlation heatmap', 'Input signature B', 'Cell filtering.'],
      },{
       pic_legend:'The density plot displays four subplots within one graph. The two histograms represent the expression level of signature A and signature B separately, while histogram2dcontour graph on the bottom left gives a more intuitive expression.',
       pic_annotation:['Tabs can be used to switch between correlation, similar genes and correlation heatmap', 'Input signature A', 'Density plot shows more details than normal(scatter) plot', 'Input signature B.', 'Cells can be colored by different groups.'],
      },{
       pic_legend:'Query all the similar genes of the selected gene. The result is sorted by the Pearson coefficient. The result is displayed via table.',
       pic_annotation:['Tabs can be used to switch between correlation, similar genes and correlation heatmap', 'Query gene here.', 'Choose preferred groupby methods.'],
      },{
       pic_legend:'A heatmap is used to display between gene similarity or cluster similarity',
       pic_annotation:['Gene-wise correlation heatmap', 'Input gene set..', 'Cell filtering.', 'Select query methods. Correlations can be calculated on either cell-by-cell or cluster-by-cluster basis.', 'Select genes or clusters to query.'],
      },{
       pic_legend:'Marker identification, which will allow us to verify the identity of certain clusters and help indentify any unknown clusters, is displayed via table with multiple statistics.',
       pic_annotation:[' Identification of all markers for each cluster is available.','"Top" limits the number of genes shown in the returned table. "Cutoff" provides a threshold and "Gene set" provides filtration genes option.', 'Choose the test methods, which we have provided t-test and wilcoxon method.', 'Show limited number of xx genes.', 'Show results of positive or negative log2 fold change, or both.', ' Sort by different criterias'],
      },{
       pic_legend:'Supervised annotations utilize scibet algorithm to annotate your dataset, the result is displayed as these four diagrams.',
       pic_annotation:['The results of annotations can be viewed as these four methods, you can click tabs to switch between functions.', 'Choose the test dataset here.'],
      },{
       pic_legend:'Use Sankey graph show the relationship.',
       pic_annotation:['The results of annotations can be viewed via four methods, you can click to switch between functions.'],
      },{
       pic_legend:'The map between your dataset index and the predicted cell types.',
       pic_annotation:'',
      },{
       pic_legend:'The Probability of the types of your datsets',
       pic_annotation:'',
      },{
       pic_legend:'Cell metadata outlines the overall information of this dataset.',
       pic_annotation:['Show the Metadata', 'Choose group by various index', 'Choose color by various index', 'Show the results as percentage or numberal'],
      },{
       pic_legend:'Here we use interactive table to display GO enrichment results, User can rank ontologies according to their interest',
       pic_annotation:['Perform genset analysis', 'Show top x number results or use value as a threshold', 'Choose species', 'Input the genesets which interest you', 'Show all genes or protein-coding genes only', 'Top number', 'The results will be sorted as your choice', 'Select GO term types.'],
      },]     
    })
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
