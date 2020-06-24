<template>
  <v-app>
    <v-main>
      <help/>
    </v-main>
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
