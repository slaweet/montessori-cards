<template>
  <div class="container">
    <div v-for="(src, name) in photos" :key="name" class="card">
      <img :src="src" :alt="name" width="210"/>
      <div class="label">{{ name.replace('./', '').replace('.jpg', '') }}</div>
    </div>
  </div>
</template>

<script>
  function importAll(r) {
    return r.keys().reduce((accumulator, key) => {
      accumulator[key] = r(key);
      return accumulator;
    }, {});
  }
  const photos = importAll(require.context('../assets/photos/', true, /\.jpg/));

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data: function() {
return {
    photos,
  };
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  max-width: 800px;
  margin-top: 2rem;
}

.card {
  display: inline-block;
  border: 1px solid #aaa;
  padding: 0.25rem;

}

.card:nth-child(n+4) {
  border-top: 0;
}

.card:nth-child(3n+2),
.card:nth-child(3n+3) {
  border-left: 0;
}

.card img {
  border-radius: 0.5rem 0.5rem 0 0;
}

.label {
  padding: 0.25rem;
  font-size: 1.65rem;
}
</style>
