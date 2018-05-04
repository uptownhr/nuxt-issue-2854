<template>
  <div class="profile">
    <h3 class="b-text is-19">
      Please fill out profile information
    </h3>
    <input v-model="profileData.profile.first_name">
  </div>
</template>
<script>
  console.log('wtf')
  export default {
    data() {
      return {
        profileData: {
          _id: null,
          profile: {
            first_name: null,
            last_name: null,
            phone: null,
            address: null,
            address2: null,
            city: null,
            state: null,
            zip: null,
            avatar_url: null
          }
        },
        avatarImageUpload: []
      }
    },

    mounted () {
      this.profileData.profile.first_name = 'james'
    }
  }
</script>
