<template>
  <div id="linkHouseModal" tabindex="-1" :style="{display: getIsLinkHouseToProfilePopupOpen ? 'block' : 'none'}"
    aria-hidden="true" class="modal fade" :class="{show: getIsLinkHouseToProfilePopupOpen}">
        <div class="modal-dialog  modal-xl modal-dialog-centered">
          <div class="modal-content">
            <div class="modal-body">
                <h3>Link profile</h3>
                <div class="link-house-wrapper">
                    <div class="section-search">
                        <div class="form-group">
                            <div class="search-icon">
                                <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <path fill-rule="evenodd" clip-rule="evenodd" d="M15.4196 18C14.7599 18 14.1273 17.7382 13.6605 17.2721L11.6842 15.2958L11.683 15.2946C11.3191 14.9225 11.0809 14.4455 11.0021 13.931C10.9232 13.4159 11.0079 12.889 11.2444 12.4246L11.3466 12.2237L10.1665 11.0435L9.95123 11.2047C8.6915 12.1474 7.12139 12.578 5.55697 12.4097C3.99255 12.2413 2.54998 11.4866 1.51966 10.2974C0.489337 9.10822 -0.0522314 7.57286 0.00397507 6.00041C0.0601816 4.42796 0.709989 2.93519 1.82259 1.82259C2.93519 0.709989 4.42796 0.0601816 6.00041 0.00397506C7.57286 -0.0522314 9.10822 0.489337 10.2974 1.51966C11.4866 2.54998 12.2413 3.99255 12.4097 5.55697C12.578 7.12139 12.1474 8.6915 11.2047 9.95123L11.0435 10.1665L12.2259 11.3489L12.4219 11.2595C12.8872 11.0473 13.4054 10.9791 13.9098 11.0637C14.4123 11.1479 14.8783 11.38 15.2484 11.7302L17.1761 13.7045L17.3982 13.4877L17.1812 13.7096C17.4183 13.9414 17.6067 14.2183 17.7354 14.524C17.864 14.8297 17.9303 15.158 17.9303 15.4896C17.9303 15.8212 17.864 16.1495 17.7354 16.4552C17.6067 16.7609 17.4183 17.0377 17.1812 17.2696L17.1789 17.2719C16.7121 17.7381 16.0793 18 15.4196 18ZM14.324 12.6065L16.3008 14.5833C16.4171 14.6988 16.51 14.8367 16.573 14.988C16.6361 15.1395 16.6687 15.3021 16.6687 15.4663C16.6687 15.6304 16.6361 15.793 16.573 15.9445C16.51 16.0957 16.4178 16.2329 16.3017 16.3484C16.1863 16.4645 16.049 16.5567 15.8979 16.6197C15.7463 16.6828 15.5838 16.7153 15.4196 16.7153C15.2554 16.7153 15.0929 16.6828 14.9413 16.6197C14.79 16.5566 14.6527 16.4643 14.5372 16.348L12.5598 14.3707C12.4436 14.2552 12.3507 14.1173 12.2876 13.966C12.2245 13.8144 12.192 13.6519 12.192 13.4877C12.192 13.3235 12.2245 13.161 12.2876 13.0094C12.3506 12.8583 12.4428 12.721 12.5589 12.6056C12.6744 12.4895 12.8116 12.3973 12.9628 12.3343C13.1143 12.2712 13.2769 12.2386 13.441 12.2386C13.6052 12.2386 13.7678 12.2712 13.9193 12.3343C14.0707 12.3974 14.2085 12.4901 14.324 12.6065ZM7.15467 11.1088C8.11973 10.9178 9.00653 10.445 9.70305 9.75027C10.1665 9.28796 10.5342 8.73877 10.7851 8.13414C11.036 7.5295 11.1652 6.88131 11.1652 6.22669C11.1652 5.57207 11.036 4.92388 10.7851 4.31925C10.5342 3.71461 10.1665 3.16542 9.70305 2.70312C9.00653 2.00836 8.11973 1.53561 7.15467 1.3446C6.18961 1.15359 5.18958 1.25288 4.28092 1.62993C3.37227 2.00699 2.59574 2.64488 2.04944 3.46304C1.50314 4.2812 1.21157 5.24291 1.21157 6.22669C1.21157 7.21047 1.50314 8.17219 2.04944 8.99035C2.59574 9.8085 3.37227 10.4464 4.28092 10.8235C5.18958 11.2005 6.18961 11.2998 7.15467 11.1088Z" fill="#C0C0C0"></path>
                                    </svg>
                                    
                            </div>
                            <input type="text" class="form-control" v-model="profile_search" placeholder="Search">
                        </div>
                    </div>

                    <div class="owener-list">
                      <div v-if="profileListFilteredComputed.length > 0" class="row g-2">
                        <div  class="col-md-3 house-link-card" v-for="(profile, index) in profileListFilteredComputed" :key="index"
                        @click="linkHouseToProfile(profile.profile_id)" data-bs-dismiss='modal'>
                          <div class="house-owner-card">
                            <div class="owner-pic"> <!-- makepic dynamic -->
                              <img src="~/assets/images/profile-pic.jpg" alt="">
                            </div>
                            <div class="owner-info">
                              <h3> {{ profile.full_name }} </h3>
                              <h4> {{ profile.designation }} </h4>
                            </div>
                          </div>
                        </div>
                        
                      </div>
                      <div v-else class="no-data">
                      <div>
                          <svg width="24" height="24"
                            viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path
                                d="M16.2421 12.694L15.969 12.9089L16.292 13.0371C18.2814 13.8266 20.0184 15.1426 21.3169 16.8441C22.6152 18.5455 23.4261 20.5681 23.6626 22.6951C23.6906 22.9572 23.614 23.2198 23.4493 23.4256C23.2869 23.6286 23.0518 23.7602 22.7941 23.7928L22.6742 23.7928L22.6729 23.7928C22.4259 23.7943 22.1871 23.7042 22.0025 23.54C21.818 23.3757 21.7008 23.1489 21.6736 22.9034L21.6736 22.9031C21.4048 20.5098 20.2636 18.2994 18.4681 16.6943C16.6726 15.0892 14.3487 14.2019 11.9404 14.2019C9.53201 14.2019 7.2081 15.0892 5.41261 16.6943C3.61712 18.2994 2.47594 20.5098 2.2071 22.9031L2.20705 22.9035C2.17786 23.1689 2.04446 23.4117 1.83619 23.5787C1.62792 23.7457 1.36184 23.8231 1.09649 23.794C0.831134 23.7648 0.588247 23.6314 0.421256 23.4231C0.338569 23.32 0.277005 23.2016 0.240078 23.0747C0.203163 22.9478 0.191589 22.8149 0.206018 22.6835C0.441369 20.5623 1.24794 18.5448 2.53974 16.8459C3.83155 15.147 5.56016 13.8306 7.54131 13.0368L7.8627 12.9081L7.5906 12.694C6.44748 11.7946 5.61312 10.5613 5.20357 9.16569C4.79402 7.77005 4.82966 6.28145 5.30553 4.907C5.78141 3.53255 6.67384 2.3406 7.85869 1.49697C9.04354 0.653348 10.4619 0.2 11.9164 0.2C13.3709 0.2 14.7892 0.653348 15.974 1.49697C17.1589 2.3406 18.0513 3.53255 18.5272 4.907C19.0031 6.28145 19.0387 7.77005 18.6292 9.16569C18.2196 10.5613 17.3852 11.7946 16.2421 12.694ZM9.14005 11.3575C9.96184 11.9066 10.928 12.1997 11.9164 12.1997C13.2417 12.1997 14.5128 11.6732 15.4499 10.736C16.3871 9.79886 16.9136 8.52779 16.9136 7.20244C16.9136 6.21408 16.6205 5.24792 16.0714 4.42613C15.5223 3.60434 14.7418 2.96383 13.8287 2.5856C12.9156 2.20737 11.9108 2.10841 10.9415 2.30123C9.97208 2.49405 9.08166 2.96999 8.38279 3.66886C7.68391 4.36774 7.20797 5.25816 7.01515 6.22753C6.82233 7.1969 6.92129 8.20168 7.29952 9.1148C7.67775 10.0279 8.31826 10.8084 9.14005 11.3575Z"
                                fill="#1B1B1B" fill-opacity="0.5" stroke="white"
                                stroke-width="0.4" />
                          </svg>
                          <h4>No Profiles</h4>
                      </div>
            </div>

                    </div>
                    <input type="hidden" :value="setprofileListFilteredComputed" />

            </div>
          </div>
        </div>
      </div>
      </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'linkHouseToProfileModal',

  data () {
    return {
      profileListFiltered: [],
      profile_search: ''

    }
  },
  watch:{
    profile_search(newValue, oldValue) {
      if(newValue.length > 2){
          this.filterProfiles(newValue)
      }else {
          this.profileListFiltered = this.allProfiles
      }
    }
  },
  computed: {
    profileListFilteredComputed() {
      return this.profileListFiltered
    },
    setprofileListFilteredComputed() {
      this.profileListFiltered = this.allProfiles
      return 1
    },
    ...mapGetters({
        getIsLinkHouseToProfilePopupOpen: 'house/getIsLinkHouseToProfilePopupOpen',
        allProfiles: 'profile/getAllProfiles'
    })
  },
  mounted() {
    this.fetchAllProfiles()
  },
  methods: {
    filterProfiles(searchedProfileName) {
        searchedProfileName = searchedProfileName.toLowerCase()
        var list = this.allProfiles

        const filtered = list.filter( (
              profile,
              index,
              array
          ) => {
              let name = profile.full_name.toLowerCase()
              if (name.includes(searchedProfileName)) {
              return true
              } else {
              return false
              }
          })
          this.profileListFiltered = filtered
    },
    async fetchAllProfiles () {
      const allProfiles = await this.$store.dispatch(
        'profile/fetchAllProfileRecords',
        {}
      )
      this.$store.commit('profile/setAllProfiles', allProfiles)
    },
    linkHouseToProfile (profileId) {
      const houseObj = this.$store.state.house.selectedHouseObj
      this.$store.dispatch(
        'house/linkHouseToProfile',
        {
          profile_id: profileId,
          house_id: houseObj.enc_house_id,
          user_id: houseObj.enc_user_id
        }
      ).then(() => {
        this.closeDeleteHouseModalPopUp()
        this.$store.dispatch('house/fetchAllHouses', {})
      })
    },
    closeDeleteHouseModalPopUp () {
      this.$store.commit('house/setIsLinkHouseToProfilePopupOpen', { isLinkHouseToProfilePopupOpen:false, selectedHouseObj: null })
    },
  },
}
</script>

<style lang="css" scoped>
  .house-link-card :hover {
    cursor: pointer;
  }
</style>