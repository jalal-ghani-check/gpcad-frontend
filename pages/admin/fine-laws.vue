<template>
    <div>
      <div class="fine-container">
            <div class="container">
                <div class="page-title-banner fine">
                    <h2><svg width="36" height="36" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M32.5414 24.0994L32.6 24.0408V23.958V12.042V11.9592L32.5414 11.9006L24.0994 3.45858L24.0408 3.4H23.958H12.042H11.9592L11.9006 3.45858L3.45858 11.9006L3.4 11.9592V12.042V23.958V24.0408L3.45858 24.0994L11.9006 32.5414L11.9592 32.6H12.042H23.958H24.0408L24.0994 32.5414L32.5414 24.0994ZM16.8686 9.66863C17.1687 9.36857 17.5757 9.2 18 9.2C18.4243 9.2 18.8313 9.36857 19.1314 9.66863C19.4314 9.96869 19.6 10.3757 19.6 10.8V18C19.6 18.4243 19.4314 18.8313 19.1314 19.1314C18.8313 19.4314 18.4243 19.6 18 19.6C17.5757 19.6 17.1687 19.4314 16.8686 19.1314C16.5686 18.8313 16.4 18.4243 16.4 18V10.8C16.4 10.3757 16.5686 9.96869 16.8686 9.66863ZM17.1111 23.8696C17.3742 23.6938 17.6835 23.6 18 23.6C18.4243 23.6 18.8313 23.7686 19.1314 24.0686C19.4314 24.3687 19.6 24.7757 19.6 25.2C19.6 25.5164 19.5062 25.8258 19.3304 26.0889C19.1545 26.352 18.9047 26.5571 18.6123 26.6782C18.3199 26.7993 17.9982 26.831 17.6879 26.7693C17.3775 26.7075 17.0924 26.5551 16.8686 26.3314C16.6449 26.1076 16.4925 25.8225 16.4307 25.5121C16.369 25.2018 16.4007 24.8801 16.5218 24.5877C16.6429 24.2953 16.848 24.0455 17.1111 23.8696ZM25.8523 0.665116C25.8528 0.665658 25.8534 0.6662 25.854 0.666742L35.3333 10.146C35.3338 10.1466 35.3343 10.1472 35.3349 10.1477C35.6277 10.4557 35.7938 10.8626 35.8 11.2874V24.7125C35.7938 25.1374 35.6277 25.5443 35.3349 25.8523C35.3343 25.8528 35.3338 25.8534 35.3333 25.854L25.854 35.3333C25.8534 35.3338 25.8528 35.3343 25.8523 35.3349C25.5443 35.6277 25.1374 35.7938 24.7125 35.8H11.2874C10.8626 35.7938 10.4557 35.6277 10.1477 35.3349C10.1472 35.3343 10.1466 35.3338 10.146 35.3333L0.666742 25.854C0.6662 25.8534 0.665658 25.8528 0.665116 25.8523C0.372325 25.5444 0.206251 25.1374 0.2 24.7126V11.2874C0.206251 10.8625 0.372339 10.4556 0.665155 10.1477L10.1477 0.665155C10.4556 0.372339 10.8625 0.206251 11.2874 0.2H24.7126C25.1374 0.206251 25.5444 0.372325 25.8523 0.665116Z" fill="white" stroke="white" stroke-width="0.4"/>
                        </svg>  
                        Fines/Laws</h2>

                    <div class="banner-btns">
                    <button v-if="isAllowedToCreateLaws"  @click="addNewLaw"   class="btn btn-success"><svg width="20" height="20" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path d="M32.5414 24.0994L32.6 24.0408V23.958V12.042V11.9592L32.5414 11.9006L24.0994 3.45858L24.0408 3.4H23.958H12.042H11.9592L11.9006 3.45858L3.45858 11.9006L3.4 11.9592V12.042V23.958V24.0408L3.45858 24.0994L11.9006 32.5414L11.9592 32.6H12.042H23.958H24.0408L24.0994 32.5414L32.5414 24.0994ZM16.8686 9.66863C17.1687 9.36857 17.5757 9.2 18 9.2C18.4243 9.2 18.8313 9.36857 19.1314 9.66863C19.4314 9.96869 19.6 10.3757 19.6 10.8V18C19.6 18.4243 19.4314 18.8313 19.1314 19.1314C18.8313 19.4314 18.4243 19.6 18 19.6C17.5757 19.6 17.1687 19.4314 16.8686 19.1314C16.5686 18.8313 16.4 18.4243 16.4 18V10.8C16.4 10.3757 16.5686 9.96869 16.8686 9.66863ZM17.1111 23.8696C17.3742 23.6938 17.6835 23.6 18 23.6C18.4243 23.6 18.8313 23.7686 19.1314 24.0686C19.4314 24.3687 19.6 24.7757 19.6 25.2C19.6 25.5164 19.5062 25.8258 19.3304 26.0889C19.1545 26.352 18.9047 26.5571 18.6123 26.6782C18.3199 26.7993 17.9982 26.831 17.6879 26.7693C17.3775 26.7075 17.0924 26.5551 16.8686 26.3314C16.6449 26.1076 16.4925 25.8225 16.4307 25.5121C16.369 25.2018 16.4007 24.8801 16.5218 24.5877C16.6429 24.2953 16.848 24.0455 17.1111 23.8696ZM25.8523 0.665116C25.8528 0.665658 25.8534 0.6662 25.854 0.666742L35.3333 10.146C35.3338 10.1466 35.3343 10.1472 35.3349 10.1477C35.6277 10.4557 35.7938 10.8626 35.8 11.2874V24.7125C35.7938 25.1374 35.6277 25.5443 35.3349 25.8523C35.3343 25.8528 35.3338 25.8534 35.3333 25.854L25.854 35.3333C25.8534 35.3338 25.8528 35.3343 25.8523 35.3349C25.5443 35.6277 25.1374 35.7938 24.7125 35.8H11.2874C10.8626 35.7938 10.4557 35.6277 10.1477 35.3349C10.1472 35.3343 10.1466 35.3338 10.146 35.3333L0.666742 25.854C0.6662 25.8534 0.665658 25.8528 0.665116 25.8523C0.372325 25.5444 0.206251 25.1374 0.2 24.7126V11.2874C0.206251 10.8625 0.372339 10.4556 0.665155 10.1477L10.1477 0.665155C10.4556 0.372339 10.8625 0.206251 11.2874 0.2H24.7126C25.1374 0.206251 25.5444 0.372325 25.8523 0.665116Z" fill="white" stroke="white" stroke-width="0.4"/>
                        </svg> 
                            Add New Law</button>
                    </div>      
                </div>


                <div class="fine-page">
                    <div class="section-search">
                        <div class="form-group">
                            <div class="search-icon">
                                <svg width="18" height="18" viewBox="0 0 18 18" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <path fill-rule="evenodd" clip-rule="evenodd" d="M15.4196 18C14.7599 18 14.1273 17.7382 13.6605 17.2721L11.6842 15.2958L11.683 15.2946C11.3191 14.9225 11.0809 14.4455 11.0021 13.931C10.9232 13.4159 11.0079 12.889 11.2444 12.4246L11.3466 12.2237L10.1665 11.0435L9.95123 11.2047C8.6915 12.1474 7.12139 12.578 5.55697 12.4097C3.99255 12.2413 2.54998 11.4866 1.51966 10.2974C0.489337 9.10822 -0.0522314 7.57286 0.00397507 6.00041C0.0601816 4.42796 0.709989 2.93519 1.82259 1.82259C2.93519 0.709989 4.42796 0.0601816 6.00041 0.00397506C7.57286 -0.0522314 9.10822 0.489337 10.2974 1.51966C11.4866 2.54998 12.2413 3.99255 12.4097 5.55697C12.578 7.12139 12.1474 8.6915 11.2047 9.95123L11.0435 10.1665L12.2259 11.3489L12.4219 11.2595C12.8872 11.0473 13.4054 10.9791 13.9098 11.0637C14.4123 11.1479 14.8783 11.38 15.2484 11.7302L17.1761 13.7045L17.3982 13.4877L17.1812 13.7096C17.4183 13.9414 17.6067 14.2183 17.7354 14.524C17.864 14.8297 17.9303 15.158 17.9303 15.4896C17.9303 15.8212 17.864 16.1495 17.7354 16.4552C17.6067 16.7609 17.4183 17.0377 17.1812 17.2696L17.1789 17.2719C16.7121 17.7381 16.0793 18 15.4196 18ZM14.324 12.6065L16.3008 14.5833C16.4171 14.6988 16.51 14.8367 16.573 14.988C16.6361 15.1395 16.6687 15.3021 16.6687 15.4663C16.6687 15.6304 16.6361 15.793 16.573 15.9445C16.51 16.0957 16.4178 16.2329 16.3017 16.3484C16.1863 16.4645 16.049 16.5567 15.8979 16.6197C15.7463 16.6828 15.5838 16.7153 15.4196 16.7153C15.2554 16.7153 15.0929 16.6828 14.9413 16.6197C14.79 16.5566 14.6527 16.4643 14.5372 16.348L12.5598 14.3707C12.4436 14.2552 12.3507 14.1173 12.2876 13.966C12.2245 13.8144 12.192 13.6519 12.192 13.4877C12.192 13.3235 12.2245 13.161 12.2876 13.0094C12.3506 12.8583 12.4428 12.721 12.5589 12.6056C12.6744 12.4895 12.8116 12.3973 12.9628 12.3343C13.1143 12.2712 13.2769 12.2386 13.441 12.2386C13.6052 12.2386 13.7678 12.2712 13.9193 12.3343C14.0707 12.3974 14.2085 12.4901 14.324 12.6065ZM7.15467 11.1088C8.11973 10.9178 9.00653 10.445 9.70305 9.75027C10.1665 9.28796 10.5342 8.73877 10.7851 8.13414C11.036 7.5295 11.1652 6.88131 11.1652 6.22669C11.1652 5.57207 11.036 4.92388 10.7851 4.31925C10.5342 3.71461 10.1665 3.16542 9.70305 2.70312C9.00653 2.00836 8.11973 1.53561 7.15467 1.3446C6.18961 1.15359 5.18958 1.25288 4.28092 1.62993C3.37227 2.00699 2.59574 2.64488 2.04944 3.46304C1.50314 4.2812 1.21157 5.24291 1.21157 6.22669C1.21157 7.21047 1.50314 8.17219 2.04944 8.99035C2.59574 9.8085 3.37227 10.4464 4.28092 10.8235C5.18958 11.2005 6.18961 11.2998 7.15467 11.1088Z" fill="#C0C0C0"/>
                                    </svg>
                            </div>
                            <input type="text" class="form-control" v-model="search_law" placeholder="Search">
                        </div>
                    </div>

                <div class="section-heading small green">
                    <h4 class="ms-3">Infraction</h4>
                </div>


                <div class="fine-list">
                    <div class="row" v-if="lawListInfractionFilteredComputed && lawListInfractionFilteredComputed.length > 0">
                        <law-item v-for="(law, index) in lawListInfractionFilteredComputed" :key="index" :law="law" @edit="addNewLaw()" />
                    </div>
                    <div v-else class="no-data">
                        <div>
                            <svg width="36" height="36" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M32.5414 24.0994L32.6 24.0408V23.958V12.042V11.9592L32.5414 11.9006L24.0994 3.45858L24.0408 3.4H23.958H12.042H11.9592L11.9006 3.45858L3.45858 11.9006L3.4 11.9592V12.042V23.958V24.0408L3.45858 24.0994L11.9006 32.5414L11.9592 32.6H12.042H23.958H24.0408L24.0994 32.5414L32.5414 24.0994ZM16.8686 9.66863C17.1687 9.36857 17.5757 9.2 18 9.2C18.4243 9.2 18.8313 9.36857 19.1314 9.66863C19.4314 9.96869 19.6 10.3757 19.6 10.8V18C19.6 18.4243 19.4314 18.8313 19.1314 19.1314C18.8313 19.4314 18.4243 19.6 18 19.6C17.5757 19.6 17.1687 19.4314 16.8686 19.1314C16.5686 18.8313 16.4 18.4243 16.4 18V10.8C16.4 10.3757 16.5686 9.96869 16.8686 9.66863ZM17.1111 23.8696C17.3742 23.6938 17.6835 23.6 18 23.6C18.4243 23.6 18.8313 23.7686 19.1314 24.0686C19.4314 24.3687 19.6 24.7757 19.6 25.2C19.6 25.5164 19.5062 25.8258 19.3304 26.0889C19.1545 26.352 18.9047 26.5571 18.6123 26.6782C18.3199 26.7993 17.9982 26.831 17.6879 26.7693C17.3775 26.7075 17.0924 26.5551 16.8686 26.3314C16.6449 26.1076 16.4925 25.8225 16.4307 25.5121C16.369 25.2018 16.4007 24.8801 16.5218 24.5877C16.6429 24.2953 16.848 24.0455 17.1111 23.8696ZM25.8523 0.665116C25.8528 0.665658 25.8534 0.6662 25.854 0.666742L35.3333 10.146C35.3338 10.1466 35.3343 10.1472 35.3349 10.1477C35.6277 10.4557 35.7938 10.8626 35.8 11.2874V24.7125C35.7938 25.1374 35.6277 25.5443 35.3349 25.8523C35.3343 25.8528 35.3338 25.8534 35.3333 25.854L25.854 35.3333C25.8534 35.3338 25.8528 35.3343 25.8523 35.3349C25.5443 35.6277 25.1374 35.7938 24.7125 35.8H11.2874C10.8626 35.7938 10.4557 35.6277 10.1477 35.3349C10.1472 35.3343 10.1466 35.3338 10.146 35.3333L0.666742 25.854C0.6662 25.8534 0.665658 25.8528 0.665116 25.8523C0.372325 25.5444 0.206251 25.1374 0.2 24.7126V11.2874C0.206251 10.8625 0.372339 10.4556 0.665155 10.1477L10.1477 0.665155C10.4556 0.372339 10.8625 0.206251 11.2874 0.2H24.7126C25.1374 0.206251 25.5444 0.372325 25.8523 0.665116Z" fill="white" stroke="white" stroke-width="0.4"/>
                            </svg>   
                            <h4>No Infraction</h4>
                        </div>
                    </div>
                </div>

                <div class="section-heading small orange">
                    <h4 class="ms-3">Misdemeanor</h4>
                </div>

                <div class="fine-list">

                    <div class="row" v-if="lawListMisdemeanorFilteredComputed && lawListMisdemeanorFilteredComputed.length > 0">
                        <law-item v-for="(law, index) in lawListMisdemeanorFilteredComputed" :key="index" :law="law" @edit="addNewLaw()" />
                    </div>
                    <div v-else class="no-data">
                        <div>
                            <svg width="36" height="36" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M32.5414 24.0994L32.6 24.0408V23.958V12.042V11.9592L32.5414 11.9006L24.0994 3.45858L24.0408 3.4H23.958H12.042H11.9592L11.9006 3.45858L3.45858 11.9006L3.4 11.9592V12.042V23.958V24.0408L3.45858 24.0994L11.9006 32.5414L11.9592 32.6H12.042H23.958H24.0408L24.0994 32.5414L32.5414 24.0994ZM16.8686 9.66863C17.1687 9.36857 17.5757 9.2 18 9.2C18.4243 9.2 18.8313 9.36857 19.1314 9.66863C19.4314 9.96869 19.6 10.3757 19.6 10.8V18C19.6 18.4243 19.4314 18.8313 19.1314 19.1314C18.8313 19.4314 18.4243 19.6 18 19.6C17.5757 19.6 17.1687 19.4314 16.8686 19.1314C16.5686 18.8313 16.4 18.4243 16.4 18V10.8C16.4 10.3757 16.5686 9.96869 16.8686 9.66863ZM17.1111 23.8696C17.3742 23.6938 17.6835 23.6 18 23.6C18.4243 23.6 18.8313 23.7686 19.1314 24.0686C19.4314 24.3687 19.6 24.7757 19.6 25.2C19.6 25.5164 19.5062 25.8258 19.3304 26.0889C19.1545 26.352 18.9047 26.5571 18.6123 26.6782C18.3199 26.7993 17.9982 26.831 17.6879 26.7693C17.3775 26.7075 17.0924 26.5551 16.8686 26.3314C16.6449 26.1076 16.4925 25.8225 16.4307 25.5121C16.369 25.2018 16.4007 24.8801 16.5218 24.5877C16.6429 24.2953 16.848 24.0455 17.1111 23.8696ZM25.8523 0.665116C25.8528 0.665658 25.8534 0.6662 25.854 0.666742L35.3333 10.146C35.3338 10.1466 35.3343 10.1472 35.3349 10.1477C35.6277 10.4557 35.7938 10.8626 35.8 11.2874V24.7125C35.7938 25.1374 35.6277 25.5443 35.3349 25.8523C35.3343 25.8528 35.3338 25.8534 35.3333 25.854L25.854 35.3333C25.8534 35.3338 25.8528 35.3343 25.8523 35.3349C25.5443 35.6277 25.1374 35.7938 24.7125 35.8H11.2874C10.8626 35.7938 10.4557 35.6277 10.1477 35.3349C10.1472 35.3343 10.1466 35.3338 10.146 35.3333L0.666742 25.854C0.6662 25.8534 0.665658 25.8528 0.665116 25.8523C0.372325 25.5444 0.206251 25.1374 0.2 24.7126V11.2874C0.206251 10.8625 0.372339 10.4556 0.665155 10.1477L10.1477 0.665155C10.4556 0.372339 10.8625 0.206251 11.2874 0.2H24.7126C25.1374 0.206251 25.5444 0.372325 25.8523 0.665116Z" fill="white" stroke="white" stroke-width="0.4"/>
                            </svg>   
                            <h4>No Misdemeanor</h4>
                        </div>
                    </div>
                </div>

                <div class="section-heading small red">
                    <h4 class="ms-3">Felony</h4>
                </div>

                <div class="fine-list">
                    <div class="row" v-if="lawListFelonyFilteredComputed && lawListFelonyFilteredComputed.length > 0">
                        <law-item v-for="(law, index) in lawListFelonyFilteredComputed" :key="index" :law="law" @edit="addNewLaw()" />
                    </div>
                    <div v-else class="no-data">
                        <div>
                            <svg width="36" height="36" viewBox="0 0 36 36" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M32.5414 24.0994L32.6 24.0408V23.958V12.042V11.9592L32.5414 11.9006L24.0994 3.45858L24.0408 3.4H23.958H12.042H11.9592L11.9006 3.45858L3.45858 11.9006L3.4 11.9592V12.042V23.958V24.0408L3.45858 24.0994L11.9006 32.5414L11.9592 32.6H12.042H23.958H24.0408L24.0994 32.5414L32.5414 24.0994ZM16.8686 9.66863C17.1687 9.36857 17.5757 9.2 18 9.2C18.4243 9.2 18.8313 9.36857 19.1314 9.66863C19.4314 9.96869 19.6 10.3757 19.6 10.8V18C19.6 18.4243 19.4314 18.8313 19.1314 19.1314C18.8313 19.4314 18.4243 19.6 18 19.6C17.5757 19.6 17.1687 19.4314 16.8686 19.1314C16.5686 18.8313 16.4 18.4243 16.4 18V10.8C16.4 10.3757 16.5686 9.96869 16.8686 9.66863ZM17.1111 23.8696C17.3742 23.6938 17.6835 23.6 18 23.6C18.4243 23.6 18.8313 23.7686 19.1314 24.0686C19.4314 24.3687 19.6 24.7757 19.6 25.2C19.6 25.5164 19.5062 25.8258 19.3304 26.0889C19.1545 26.352 18.9047 26.5571 18.6123 26.6782C18.3199 26.7993 17.9982 26.831 17.6879 26.7693C17.3775 26.7075 17.0924 26.5551 16.8686 26.3314C16.6449 26.1076 16.4925 25.8225 16.4307 25.5121C16.369 25.2018 16.4007 24.8801 16.5218 24.5877C16.6429 24.2953 16.848 24.0455 17.1111 23.8696ZM25.8523 0.665116C25.8528 0.665658 25.8534 0.6662 25.854 0.666742L35.3333 10.146C35.3338 10.1466 35.3343 10.1472 35.3349 10.1477C35.6277 10.4557 35.7938 10.8626 35.8 11.2874V24.7125C35.7938 25.1374 35.6277 25.5443 35.3349 25.8523C35.3343 25.8528 35.3338 25.8534 35.3333 25.854L25.854 35.3333C25.8534 35.3338 25.8528 35.3343 25.8523 35.3349C25.5443 35.6277 25.1374 35.7938 24.7125 35.8H11.2874C10.8626 35.7938 10.4557 35.6277 10.1477 35.3349C10.1472 35.3343 10.1466 35.3338 10.146 35.3333L0.666742 25.854C0.6662 25.8534 0.665658 25.8528 0.665116 25.8523C0.372325 25.5444 0.206251 25.1374 0.2 24.7126V11.2874C0.206251 10.8625 0.372339 10.4556 0.665155 10.1477L10.1477 0.665155C10.4556 0.372339 10.8625 0.206251 11.2874 0.2H24.7126C25.1374 0.206251 25.5444 0.372325 25.8523 0.665116Z" fill="white" stroke="white" stroke-width="0.4"/>
                            </svg>   
                            <h4>No Felony</h4>
                        </div>
                    </div>
                </div>
            </div>
            <add-new-law-modal :show-modal="showAddModalComputed" @close="closeAddModal" />
            <law-detail-modal />
            <delete-law-modal @fetchLaws="fetchAllLaws" />

        </div>
      </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex'
import AddNewLawModal from '~/components/fine-laws/AddNewLawModal.vue'
import lawItem from '~/components/fine-laws/fineCardItem.vue'
import LawDetailModal from '~/components/fine-laws/lawDetailModal.vue'
import DeleteLawModal from '~/components/fine-laws/deleteLawModal.vue'
export default {
  components: { lawItem, AddNewLawModal, LawDetailModal, LawDetailModal, DeleteLawModal },
  name: 'FineLaws',
  layout: 'master',
  middleware: ['lawsMW'],
  data () {
    return {
      isAddModalOpen: false  ,
      lawsList: [],
    //   lawsListFiltered: [],
      lawListInfraction: [],
      lawListInfractionFiltered: [],
      lawListFelony: [],
      lawListFelonyFiltered: [],
      lawListMisdemeanor: [],
      lawListMisdemeanorFiltered: [],
      search_law: "", 
    }
  },
  watch: {
        search_law(newValue, oldValue){
          if(newValue.length > 2){
              this.filterLaws(newValue)
          }else {
                this.lawListFelonyFiltered = this.lawsList.felony
                this.lawListMisdemeanorFiltered = this.lawsList.misdemeanor
                this.lawListInfractionFiltered = this.lawsList.infraction


          }
        }
  },
  computed: {
    lawListInfractionFilteredComputed() {
      return this.lawListInfractionFiltered
    },
    lawListFelonyFilteredComputed() {
      return this.lawListFelonyFiltered
    },
    lawListMisdemeanorFilteredComputed() {
      return this.lawListMisdemeanorFiltered
    },
    showAddModalComputed() {
      return this.isAddModalOpen
    },
     ...mapGetters({
      isAllowedToCreateLaws: 'auth/isAllowedToCreateLaws'
    }),
  },
  mounted () {
    this.$store.commit('setActiveTab', 'users')
    this.fetchAllLaws()
  },
  methods: {
    async fetchAllLaws(){
      this.lawsList = await this.$store.dispatch(
        'law/fetchAllLaws',
        {}
      )
      this.lawListInfraction = this.lawsList.infraction
      this.lawListInfractionFiltered = this.lawsList.infraction
      this.lawListFelony = this.lawsList.felony
      this.lawListFelonyFiltered = this.lawsList.felony
      this.lawListMisdemeanor = this.lawsList.misdemeanor
      this.lawListMisdemeanorFiltered = this.lawsList.misdemeanor

    },
    closeAddModal() {
      this.isAddModalOpen = false
      this.$store.commit('law/setSelectedLaw', null)
      this.fetchAllLaws()

    },
    addNewLaw() {
      this.isAddModalOpen = true  

    },
    filterLaws(lawTitleSearched) {
        lawTitleSearched = lawTitleSearched.toLowerCase()
        var listInfraction = this.lawListInfraction
        var listFelony = this.lawListFelony
        var listMisdemeanor = this.lawListMisdemeanor

        const filteredInfraction = listInfraction.filter( (
            law,
            index,
            array
        ) => {
            let title = law.law_title.toLowerCase()
            if (title.includes(lawTitleSearched)) {
            return true
            } else {
            return false
            }
        })

        const filteredfelony = listFelony.filter( (
            law,
            index,
            array
        ) => {
            let title = law.law_title.toLowerCase()
            if (title.includes(lawTitleSearched)) {
            return true
            } else {
            return false
            }
        })

        const filteredmisdemeanor = listMisdemeanor.filter( (
            law,
            index,
            array
        ) => {
            let title = law.law_title.toLowerCase()
            if (title.includes(lawTitleSearched)) {
            return true
            } else {
            return false
            }
        })


        this.lawListInfractionFiltered = filteredInfraction
        this.lawListFelonyFiltered = filteredfelony
        this.lawListMisdemeanorFiltered = filteredmisdemeanor

    }
  }
}
</script>

<style lang='css' scoped>
  .fine-page {
    margin-bottom: 30px;
}
.page-title-banner.fine {
    background: url('~/assets/images/fine-banner.png') no-repeat;
    background-size: 100% !important;
}
.fine-page .section-search {
    margin-top: 20px;
}
.fine-page .section-search  .form-control {
    height: 50px !important;
}
.fine-page .section-search .search-icon {
    left: 17px;
    top: 13px;
}

.fine-list .fine-card {
    margin-bottom: 20px;
    max-width: 100%;

}
.page-title-banner .cover-btns {
    align-self: flex-end;
    margin-left: auto;
    text-align: right;
}
.page-title-banner .cover-btns  .btn {
    min-width:150px;
    margin-left: 5px;
}
</style>