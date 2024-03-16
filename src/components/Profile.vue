<template>
    <h2>{{ profile.name }}</h2>
    <h4>{{ profile.bio }}</h4>
    <img :src="profile.avatar_url" alt="Avatar" width="80" />
</template>

<script>

import axios from 'axios';

export default {
    name: 'Profile',
    data() {
        return {
            profile: {}
        };
    },

  methods: {
    loadProfile() {
      axios.get('https://api.github.com/users/fabiovige')
        .then(response => {
          this.profile = response.data;
          console.log(this.profile);
        })
        .catch(error => {
          console.log(error);
        });
    }
  },
  mounted() {
    this.loadProfile();
  }
};
</script>