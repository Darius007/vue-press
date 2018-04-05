<template>
  <nav>

    <h1>
      <router-link
        :to="{
          name: 'home',
        }">
        Vuepress
      </router-link>
    </h1>

    <div>
      <p>
        Currently streaming content from <a :href="sourceURL">{{ sourceName[2] }}</a>.
      </p>

      <button @click="showUpdater">
        Change Endpoint
      </button>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'TopBar',

  data () {
    return {}
  },

  computed: {
    splitEndpoint: function () {
      return this.$store.state.endpoint.split('wp-json');
    },

    sourceURL: function () {
      return this.splitEndpoint[0];
    },
    sourceName: function () {
      return this.$store.state.endpoint.split('/');
    }
    
  },

  methods: {
    showUpdater: function () {
      this.$emit('showUpdater');
    }
  }
}

</script>

<style scoped lang="scss">
  nav {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    text-align: center;
    align-items: center;
    margin-bottom: 1rem;
    background: rgba($gray--light, .9);
    padding: 1rem 2rem;
    border-bottom: 2px solid darken($gray--light, 5%);

    @include media($small) {
      flex-direction: row;
    }
  }

  div {
    display: flex;
    align-items: center;
    flex-direction: column;

    @include media($mobile) {
      flex-direction: row;
    }
  }

  button {
    @include media($mobile) {
      margin: 0 0 0 1rem;
    }
  }

  h1 {
    margin: 0;
  }

  a {
    font-weight: bold;
  }

  p {
    text-align: center;
    margin: .5rem 0 1rem;

    @include media($mobile) {
      margin: 0;
      text-align: right;
    }
  }
</style>

