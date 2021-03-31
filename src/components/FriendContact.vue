<template>
  <li>
    <h2>{{ name }} {{ friendIsFavorite === "1" ? "(Favorite)" : "" }}</h2>
    <button @click="toggleDetails()">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <button @click="toggleFavorite()">Toggle Favorite</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAdress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: ["name", "phoneNumber", "emailAdress", "isFavorite"],
  data() {
    return {
      detailsAreVisible: false,
      friend: {
        id: "manuel",
        name: "Manuel Lorenz",
        phone: "0123 45678 90",
        email: "manuel@localhost.com",
      },
      friendIsFavorite: this.isFavorite,
    };
  },
  methods: {
    toggleFavorite() {
      if (this.friendIsFavorite === "1") {
        this.friendIsFavorite = "0";
      } else {
        this.friendIsFavorite = "1";
      }
    },
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
  },
};
</script>
