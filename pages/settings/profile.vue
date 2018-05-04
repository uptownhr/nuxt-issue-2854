<template>
  <div class="profile">
    <h3 class="b-text is-19">
      Please fill out profile information
    </h3>
    <input v-model="profileData.profile.first_name" />
  </div>
</template>
<script type="text/ecmascript-6">

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
    },

    methods: {
      handle_upload_files(files) {
        if(!files) return false;
        let _this = this;
        files.forEach(function(e) {
          _this.avatarImageUpload.push(e);
        })
      },
      deleteDropFile(index) {
        this.avatarImageUpload.splice(index, 1)
      },
      updateProfile() {
        if(this.avatarImageUpload[0]) {
          this.profileData.profile.avatar_url = this.avatarImageUpload[0].url;
        }
        this.$store.dispatch('users/update', this.profileData)
          .then( res => {
            this.$toast.open({
              type: 'is-success',
              position: 'is-bottom',
              message: 'Account Updated'
            })
          })
      }
    }
  }
</script>
