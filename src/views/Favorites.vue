<template>
  <v-list>
    <v-subheader v-if="!favorites.length">Your favorites list is empty</v-subheader>
    <div v-else>
      <v-subheader>Your favorites</v-subheader>
      <v-list-item v-for="(dog, index) in favorites" :key="index" @click="{}">
        <v-list-item-avatar>
          <img :src="dog.img">
        </v-list-item-avatar>
        <v-list-item-content>{{dog.name}}</v-list-item-content>
        <v-btn class="focus" @click="removeFromFavorites(dog)">
          <v-icon>delete</v-icon>
        </v-btn>
      </v-list-item>
      <v-btn to="/form">Adopt</v-btn>
    </div>
  </v-list>
</template>

<script>
import { mapActions } from "vuex";

export default {
  computed: {
    favorites() {
      return this.$store.state.favorites;
    }
  },
  methods: {
    ...mapActions(["removeFromFavorites"])
  }
};
</script>
