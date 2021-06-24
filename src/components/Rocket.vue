<template>
  <div id="apol">
    <button @click="$router.go(-1)">Return</button>

    <div v-if="rocket">
      <h2>{{ rocket.name }}</h2>
      {{ rocket.description }}
    </div>
  </div>
</template>

<script>
import gql from "graphql-tag";

const query = gql`
  query getRockets($id: ID!) {
    rocket(id: $id) {
      id
      name
      description
    }
  }
`;
export default {
  props: {
    id: {
      type: String,
    },
  },

  apollo: {
    rocket: {
      query,
      variables() {
        return {
          id: this.id,
        };
      },
    },
  },
};
</script>

<style lang="scss" scoped>
#apol {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  justify-content: center;
  align-items: center;
}
</style>
