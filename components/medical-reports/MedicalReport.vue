<template>
  <div>
    <div :style="{display: isMedicalReportPopupOpen ? 'block' : 'none'}" v-if="isMedicalReportPopupOpen && selectedMedicalReportObject"
    class="modal fade" id="medicalReport" tabindex="-1"  aria-hidden="true" :class= "{show: isMedicalReportPopupOpen}">
        <div class="modal-dialog report-modal modal-dialog-centered ">
          <div class="modal-content">
            <div class="modal-body">
                <header style="background-color:#000;color:#fff;">
                  <span  class="close-button topright" @click="closePoliceReportModalPopUp()">&times;</span>
                </header>
                <div class="report-header">
                    <div class="header-logo">
                        <img src="../../assets/images/medical-report-logo.png" alt="">
                    </div>
                    <div class="report-title">
                        <h3>Medical Report</h3>
                        <h4>{{ selectedMedicalReportObject.profile_name }} // {{ selectedMedicalReportObject.problem_started_at }}</h4>
                    </div>  
                </div>
                <div class="report-body">
                    <h4>Problem Description:</h4>
                    <p>{{ selectedMedicalReportObject.problem_description }}</p>
                
                    <div class="border-entries">
                        <div class="row g-0">
                            <div class="col-md-6">
                                <h3>When did this problem start?</h3>
                                <h4>{{ selectedMedicalReportObject.problem_started_at }}</h4>
                            </div>
                            <div class="col-md-6">
                                <h3>Cause of Current Problem:</h3>
                                <h4>{{ selectedMedicalReportObject.problem_cause }}</h4>
                            </div>
                        </div>
                    </div>
                        <h4 class="mb-0 mt-4">Past Medical History:</h4>
                        <p>{{ selectedMedicalReportObject.medical_history }}</p>

                     
                        <div class="border-entries">
                            <div class="row g-0">
                                <div class="col-md-4">
                                    <h3>Surgeries:</h3>
                                    <h4>{{ selectedMedicalReportObject.surgery_name }}</h4>
                                </div>
                                <div class="col-md-4">
                                    <h3>Surgery Year:</h3>
                                    <h4>{{ selectedMedicalReportObject.surgery_year }}</h4>
                                </div>
                                <div class="col-md-4">
                                    <h3>Surgery Complications:</h3>
                                    <h4>{{ selectedMedicalReportObject.surgery_complication }}</h4>
                                </div>
                            </div>
                        </div>
                        <h4 class="mt-4">Surgery Description:</h4>
                        <p>{{ selectedMedicalReportObject.surgery_description }}</p>
                        
                        <div class="border-entries">
                            <div class="row g-0">
                                <div class="col-md-4">
                                    <h3>Medications:</h3>
                                    <h4>{{ selectedMedicalReportObject.medication_name }}</h4>
                                </div>
                                <div class="col-md-4">
                                    <h3>Medications Done:</h3>
                                    <h4>{{ selectedMedicalReportObject.medication_done }}</h4>
                                </div>
                                <div class="col-md-4">
                                    <h3>Reason For Medications:</h3>
                                    <h4>{{ selectedMedicalReportObject.medication_reason }}</h4>
                                </div>
                            </div>
                        </div>
                        <h4 class="mt-4">Medication Description:</h4>
                        <p>{{ selectedMedicalReportObject.medication_description }}</p>
                        <div class="border-entries">
                            <div class="row g-0" style="border-bottom: none;">
                                <div class="col-md-4">
                                    <h3>Allergies:</h3>
                                    <h4>{{ selectedMedicalReportObject.allergies_details }}</h4>
                                </div>
                            
                            </div>
                        </div>
                        <div class="border-entries">
                            <div class="row g-0">
                                <div class="col-md-3">
                                    <h3>Latex:</h3>
                                    <h4>{{ selectedMedicalReportObject.allergies_latex }}</h4>
                                </div>
                                <div class="col-md-3">
                                    <h3>Iodine:</h3>
                                    <h4>{{ selectedMedicalReportObject.allergies_iodine }}</h4>
                                </div>
                                <div class="col-md-3">
                                    <h3>Bromine:</h3>
                                    <h4>{{ selectedMedicalReportObject.allergies_bromine }}</h4>
                                </div>
                                <div class="col-md-3">
                                    <h3>Other:</h3>
                                    <h4>{{ selectedMedicalReportObject.allergies_other }}</h4>
                                </div>
                            </div>
                        </div>
                        <h4 class="mt-4 mb-0">Do you have any religious/cultural views that will affect your treatment?</h4>
                        <p> {{ selectedMedicalReportObject.personal_views }}</p>
                
                </div>
            </div>
          </div>
        </div>
      </div>
      <div v-if="isMedicalReportPopupOpen" class="modal-backdrop fade show" />
  </div>  
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'medicalReportDetails',
  computed: {
    ...mapGetters({
        isMedicalReportPopupOpen: 'report/getIsMedicalReportPopupOpen',
        selectedMedicalReportObject: 'report/getSelectedMedicalReportObject'
    })
  },
  methods: {
    closePoliceReportModalPopUp () {
      this.$store.commit('report/setIsMedicalReportPopupOpen', false)
      this.$store.commit('report/setSelectedMedicalReport', null)
    }
  },
}
</script>

<style lang="css" scopted>
    .modal {
        overflow-y: auto;
    }

    .close-button {
  border: none;
  display: inline-block;
  padding: 8px 16px;
  vertical-align: middle;
  overflow: hidden;
  text-decoration: none;
  color: inherit;
  background-color: inherit;
  text-align: center;
  cursor: pointer;
  white-space: nowrap
}

.topright {
  position: absolute;
  right: 0;
  top: 0
}

</style>