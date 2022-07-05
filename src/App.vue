<template>
  <div class="container">
    <KeySearch/>
    <ContentsList/>
  </div>
</template>
<script>

import ContentsList from "@/components/ContentsList";
import KeySearch from "@/components/KeySearch";

export default {
  name: 'App',
  components: {ContentsList, KeySearch}
}
</script>

<style>

</style>
