<template>
  <v-app>
    <v-content>
      <help/>
    </v-content>
  </v-app>
</template>

<script>
import help from './components/help';

export default {
  name: 'App',

  components: {
    help,
  },

  data: () => ({
    //
  }),
};
</script>
