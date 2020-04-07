<script>
  export default {
    props: ['gifts'],
    name: 'Preview',
  };
</script>

<template>
  <div>
    <ul>
      <li
        v-for="gif in gifts"
        :key="gif.id">
        <img :src="gif.images.fixed_height.url"/>
      </li>
    </ul>

  </div>
</template>

<style scoped>
  li {
    list-style: none;
    float: left;
    margin: 20px;
  }

</style>
