<template lang="pug">
  v-container(fill-height)
    v-row
      v-col
        h1 Error
</template>

<script>
import headMeta from '~/utils/head-meta';
export default {
  layout: 'default',
  props: {
    error: {
      type: Object,
      default: null,
    },
  },
  data () {
    console.log(this.error);
    return {
      pageNotFound: '404 Not Found',
      otherError: 'An error occurred',
    };
  },
  computed: {
    backBtnClasses () {
      return ['font-xs', 'font-weight-bold', 'text-capitalize'];
    },
  },
  head () {
    if (this.error.statusCode === 404) {
      return headMeta({
        title: 'Vaxert.com - Page Not Found',
        description: 'Either the page has been removed or has a new link.',
      });
    } else {
      return {
        title: `Vaxert.com - ${this.otherError}`,
        description: this.otherError,
      };
    }
  },
};
</script>
