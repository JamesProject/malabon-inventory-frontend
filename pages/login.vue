<template>
    <div class="tw-w-screen tw-h-screen tw-flex tw-flex-col tw-p-8">
        <div class="tw-flex-0">
            <div class="tw-flex tw-flex-row tw-items-center tw-gap-2 ">
                <img src="~/assets/logo/logo.png" class="tw-w-12 tw-h-12">
                <div class="tw-font-semibold tw-text-2xl tw-font-ceng" style="font-weight: 600;">
                    City of Malabon
                </div>
            </div>
        </div>
        <div class="tw-flex tw-flex-1">
            <div class="relative tw-m-auto tw-overflow-hidden tw-rounded-md tw-border tw-border-theme">
                    <v-sheet min-height="auto" min-width="420">
                        <div class="tw-w-full tw-h-full tw-flex tw-flex-col tw-p-8 tw-pb-16">
                            <div class="tw-flex tw-flex-col tw-flex-0 ">
                                <img src="~/assets/logo/logo.png" class="tw-mx-auto tw-w-14 tw-h-14">
                            </div>
                            <div>
                                <div class="tw-flex tw-flex-col tw-text-center">
                                    <div class="tw-text-2xl tw-font-semibold tw-mt-4  tw-font-ceng">Sign in</div>
                                    <div class="tw-text-base  tw-mt-4">Malabon ASI System</div>
                                </div>
                            </div>
                            <div class=" tw-mt-3">

                                <v-text-field v-model="data.email" color="#FF5976"  :error="error" @input="error=false" dense label="Username" outlined required></v-text-field>
                                <v-text-field v-model="data.password" color="#FF5976"
                                @click:append="show1 = !show1"
                                :type="show1 ? 'text' : 'password'"
                                :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'" :error="error" @input="error=false" dense label="Password" outlined   required>
                                </v-text-field>

                                <v-checkbox v-model="data.remember_me" dense label="Keep me signed in" :value="true"></v-checkbox>

                                <v-btn :loading="loading" block @click="testLogin()" color="#FF5976">

                                    <template #default>
                                        <span class="tw-text-white">
                                            Sign in
                                        </span>
                                    </template>
                                </v-btn>
                                <v-sheet class="tw-mt-5">
                                    Forgot Password?
                                </v-sheet>
                            </div>
                            <div></div>
                        </div>
                    </v-sheet>
            </div>
        </div>
        <div class="tw-flex-0"></div>
    </div>
</template>
<script>
    export default {
        layout: 'unauthorize',
        data() {
            return {
                loading: false,
                error:false,
                show1:false,
                data:{
                  password:'',
                  email:'',
                  remember_me:false
                }
            }
        },
       
        methods: {
            testLogin() {
              this.loading = true
               this.error = false
              this.$auth.loginWith('laravelPassport',{
                   data:this.data
               }).then(()=>{
                   this.$router.push({name:'index'})
               }).catch(()=>{
                  this.error = true
                  this.loading = false
               })


            }
        }
    }
</script>
