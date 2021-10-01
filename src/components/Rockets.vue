<template>
  <div id="apol">
    <h1>Apollo GraphQl</h1>

    <ul>
      <li v-for="rocket in rockets" :key="rocket.id">
        <router-link :to="{ name: 'Rocket', params: { id: rocket.id } }">
          🗺 {{ rocket.name }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import gql from "graphql-tag";

const query = gql`
  query getRockets {
    rockets {
      id
      name
    }
  }
`;
export default {
  apollo: {
    rockets: {
      query,
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
