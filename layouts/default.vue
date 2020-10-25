<template>
  <div>
    <pm-header />
    <Nuxt />
    <pm-footer />
  </div>
</template>

<script>

import PmHeader from "~/components/Header";
import PmFooter from "~/components/Footer";

export default {
  
  components: { PmHeader, PmFooter }

}
</script>