<template>
  <div>
    <div v-if="getIsEditHousePopupOpen" aria-hidden="true" :style="{display: getIsEditHousePopupOpen ? 'block' : 'none'}" :key="selectedHouseObj"
        class="modal fade" id="editHouseModal" tabindex="-1" :class= "{show: getIsEditHousePopupOpen}">
            <div class="modal-dialog edit-house-modal modal-dialog-centered">
              <div class="modal-content">
                <div class="modal-body">

                    <notification-bar />
                    
                    <div class="mb-3">
                      
                      <div class="house-pic">
                        <div class="add-picture">
                            <!-- <label for="housePic"><img src="~/assets/images/plus-icon.svg" height="150" width="150"></label> -->
                            <ProfileImageUploader
                              :profile-image="houseImageComputed"
                              @file-uploaded="fileUploaded"
                            />
                        </div>
                        <div
                          v-if="$v.image.$error && !$v.image.required"
                          class="error"
                          >
                              Image is required
                        </div>
                      </div>
                    </div>
                    
                    <div class="mb-3">
                        <input type="text" v-model="houseName" maxlength="255" class="form-control" placeholder="Name">
                        <div
                          v-if="$v.houseName.$error && !$v.houseName.required"
                          class="error"
                          >
                              Name is required
                        </div>
                    </div>
                    <div class="mb-3">
                        <input type="text" maxlength="11" v-model="housePrice" class="form-control" placeholder="Price">
                        <div
                          v-if="$v.housePrice.$error && !$v.housePrice.required"
                          class="error"
                          >
                              Price is required
                        </div>
                    </div>
                    <div class="row g-2">
                        <div class="col-sm-6">
                            <div class="d-grid">
                                <button class="btn btn-danger" @click="closeEditHouseModalPopUp()" type="button"><svg width="17" height="18" viewBox="0 0 17 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <path d="M6.3 14.4C6.5387 14.4 6.76761 14.3052 6.9364 14.1364C7.10518 13.9676 7.2 13.7387 7.2 13.5V8.1C7.2 7.8613 7.10518 7.63239 6.9364 7.4636C6.76761 7.29482 6.5387 7.2 6.3 7.2C6.06131 7.2 5.83239 7.29482 5.6636 7.4636C5.49482 7.63239 5.4 7.8613 5.4 8.1V13.5C5.4 13.7387 5.49482 13.9676 5.6636 14.1364C5.83239 14.3052 6.06131 14.4 6.3 14.4ZM15.3 3.6H11.7V2.7C11.7 1.98392 11.4155 1.29716 10.9092 0.790812C10.4028 0.284464 9.71608 0 9 0H7.2C6.48392 0 5.79716 0.284464 5.29081 0.790812C4.78446 1.29716 4.5 1.98392 4.5 2.7V3.6H0.9C0.661305 3.6 0.432387 3.69482 0.263604 3.8636C0.0948211 4.03239 0 4.2613 0 4.5C0 4.73869 0.0948211 4.96761 0.263604 5.1364C0.432387 5.30518 0.661305 5.4 0.9 5.4H1.8V15.3C1.8 16.0161 2.08446 16.7028 2.59081 17.2092C3.09716 17.7155 3.78392 18 4.5 18H11.7C12.4161 18 13.1028 17.7155 13.6092 17.2092C14.1155 16.7028 14.4 16.0161 14.4 15.3V5.4H15.3C15.5387 5.4 15.7676 5.30518 15.9364 5.1364C16.1052 4.96761 16.2 4.73869 16.2 4.5C16.2 4.2613 16.1052 4.03239 15.9364 3.8636C15.7676 3.69482 15.5387 3.6 15.3 3.6ZM6.3 2.7C6.3 2.46131 6.39482 2.23239 6.5636 2.0636C6.73239 1.89482 6.96131 1.8 7.2 1.8H9C9.2387 1.8 9.46761 1.89482 9.6364 2.0636C9.80518 2.23239 9.9 2.46131 9.9 2.7V3.6H6.3V2.7ZM12.6 15.3C12.6 15.5387 12.5052 15.7676 12.3364 15.9364C12.1676 16.1052 11.9387 16.2 11.7 16.2H4.5C4.26131 16.2 4.03239 16.1052 3.8636 15.9364C3.69482 15.7676 3.6 15.5387 3.6 15.3V5.4H12.6V15.3ZM9.9 14.4C10.1387 14.4 10.3676 14.3052 10.5364 14.1364C10.7052 13.9676 10.8 13.7387 10.8 13.5V8.1C10.8 7.8613 10.7052 7.63239 10.5364 7.4636C10.3676 7.29482 10.1387 7.2 9.9 7.2C9.66131 7.2 9.43239 7.29482 9.2636 7.4636C9.09482 7.63239 9 7.8613 9 8.1V13.5C9 13.7387 9.09482 13.9676 9.2636 14.1364C9.43239 14.3052 9.66131 14.4 9.9 14.4Z" fill="white"/>
                                    </svg>
                                    Discard</button>
                            </div>
                        </div>
                        <div class="col-sm-6">
                            <div class="d-grid">
                                <button class="btn btn-success" type="button"
                                  @click="updateHouseInfo()"
                                >
                                <svg width="26" height="26" viewBox="0 0 26 26" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <path d="M6.36394 19.3641C7.62262 20.6227 9.22626 21.4799 10.9721 21.8272C12.7179 22.1744 14.5275 21.9962 16.1721 21.315C17.8166 20.6338 19.2222 19.4803 20.2111 18.0002C21.2001 16.5202 21.7279 14.7801 21.7279 13.0001C21.7279 11.2201 21.2001 9.48002 20.2111 7.99997C19.2222 6.51993 17.8166 5.36638 16.1721 4.68519C14.5275 4.004 12.7179 3.82578 10.9721 4.17304C9.22626 4.52031 7.62262 5.37748 6.36394 6.63615C5.52822 7.47187 4.86528 8.46403 4.41299 9.55596C3.9607 10.6479 3.7279 11.8182 3.72791 13.0001C3.72791 14.182 3.9607 15.3523 4.41299 16.4443C4.86528 17.5362 5.52822 18.5283 6.36394 19.3641ZM17.8191 7.90894C18.826 8.91588 19.5117 10.1988 19.7896 11.5955C20.0674 12.9921 19.9248 14.4398 19.3798 15.7554C18.8349 17.0711 17.912 18.1955 16.728 18.9867C15.544 19.7778 14.1519 20.2001 12.7279 20.2001C11.3039 20.2001 9.91183 19.7778 8.7278 18.9867C7.54376 18.1955 6.62092 17.0711 6.07597 15.7554C5.53102 14.4398 5.38844 12.9921 5.66625 11.5955C5.94406 10.1988 6.6298 8.91588 7.63674 7.90894C8.987 6.55868 10.8183 5.80011 12.7279 5.80011C14.6375 5.80011 16.4688 6.55868 17.8191 7.90894ZM8.04593 13.8436C8.89445 14.6921 9.74298 15.5407 10.5915 16.3892C10.7603 16.558 10.9892 16.6528 11.2279 16.6528C11.4666 16.6528 11.6955 16.558 11.8643 16.3892C15.1585 13.095 13.6613 14.5922 16.9555 11.298C17.1243 11.1292 17.2191 10.9003 17.2191 10.6616C17.2191 10.4229 17.1243 10.194 16.9555 10.0252C16.7867 9.85645 16.5578 9.76163 16.3191 9.76163C16.0804 9.76163 15.8515 9.85645 15.6827 10.0252L11.2279 14.48L9.31872 12.5708C9.14993 12.402 8.92102 12.3072 8.68232 12.3072C8.44363 12.3072 8.21471 12.402 8.04593 12.5708C7.87714 12.7396 7.78232 12.9685 7.78232 13.2072C7.78232 13.4459 7.87714 13.6748 8.04593 13.8436Z" fill="white"/>
                                    </svg>
                                    
                                    Update Details</button>
                            </div>
                        </div>
                    </div>

                </div>
              </div>
            </div>
    </div>
    <div v-if="getIsEditHousePopupOpen" class="modal-backdrop fade show" />
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import { required, requiredIf } from 'vuelidate/lib/validators'

export default {
  name: 'editHouseModal',
  data() {
    return {
      housePrice: '',
      houseName: '',
      image: '',
      houseImage: ""
    }
  },
  validations: {
    houseName: {
      required,
    },
    housePrice: {
      required
    },
    image: {
      required
    },

  },

  computed: {
    ...mapGetters({
        getIsEditHousePopupOpen: 'house/getIsEditHousePopupOpen',
        // selectedHouseObject: 'house/getSelectedHouseObject'
    }),
    selectedHouseObj () {
      const obj = this.$store.getters['house/getSelectedHouseObject']
      if(obj) {
        this.housePrice = obj.non_formatted_price
        this.houseName = obj.house_name,
        this.houseImage = obj.image_base64
      }
    },
    houseImageComputed() {
      return this.houseImage
    }
  },
  methods: {
    closeEditHouseModalPopUp () {
      this.housePrice = ''
      this.houseName = ''
      this.houseImage = ""
      this.image = ""
      this.$v.$reset()
      this.$store.commit('house/setIsEditHousePopupOpen', { isEditHousePopupOpen: false, selectedHouseObj: null , selectedindex: 0 })
    },
    updateHouseInfo(){
      const houseObj = this.$store.state.house.selectedHouseObj
      const houseindex = this.$store.state.house.selectedindex
      this.$v.$touch()
      if (!this.$v.$invalid) {
        this.$store.dispatch(
          'house/manageHouse',
          {
            house_id: houseObj ? houseObj.enc_house_id : '',
            house_name: this.houseName,
            price: this.housePrice,
            image: this.image,
            selectedindex: houseindex
            
          }
        ).then((response) => {
          this.closeEditHouseModalPopUp()
          this.$store.dispatch('house/fetchAllHouses', {})
        })
      }
    },
    fileUploaded(files) {
      this.image = files
    },

  },
}
</script>
<style lang="css">
.filepond--wrapper {
  width: 100% !important;
} 
.edit-house-modal .form-control {
  font-size: 14px;
}
.filepond--root[data-style-panel-layout~='circle'] .filepond--file [data-align*='right'] {
  right: 10px !important;
  top: 10px;
}
.filepond--credits {
  font-size: 0 !important;
}
.filepond--root[data-style-panel-layout~=circle],
.filepond--root[data-style-panel-layout~=circle] .filepond--image-preview-wrapper {
  border-radius: 0 !important;
}
</style>
