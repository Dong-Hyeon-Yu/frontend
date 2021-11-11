<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="project"> <!-- 경고창 -->
      <template v-slot:activator="{ on }"> <!-- on 은 액션창 생성 명령어 --> 
        <v-btn outlined color="white" dark v-on="on" > Login </v-btn>
      </template>







      <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="7">
            <v-card class="elevation-12">
               <v-window v-model="step">
               <v-window-item :value="1">
                  <v-row>
                    <v-col cols="12" md="8">
                     <v-card-text class="mt-50">
                       
                       <h1 class="text-center display-2 teal--text text--lighten-3">Sign in to MapDuck</h1>
                       <div class="text-center mt-3" mt-4>
                         <v-btn class="mx-2" fab-color ="black" outlined>
                           <v-icon>fab fa-neos</v-icon>
                         </v-btn>

                         <v-btn class="mx-2" fab-color="black" outlined>
                           <v-icon>fab fa-google-plus-g</v-icon>
                         </v-btn>

                         <v-btn class="mx-2" fab-color="black" outlined>
                           <v-icon>fab fa-facebook-f</v-icon>
                         </v-btn>

                       </div>
                       <h4 class="text-center mlt-4">Ensure your email for registration</h4>
                       <v-form>




                         <div class="protected" v-if="loginSuccess">
                          <h1>
                         <b-badge variant="success">보안 사이트에 대한 액세스가 허용되었습니다</b-badge>
                          </h1>
                          <h5>로그인 성공!</h5>
                          </div>

                          <div class="unprotected" v-else-if="loginError">
                            <h1>
                             <b-badge variant="danger">이 페이지에 대한 접근 권한이 없습니다.</b-badge>
                             </h1>
                                <h5>로그인 실패!</h5>
                              </div>

                              <div class="unprotected" v-else>
                              <h1>
                            <b-badge  variant="info">
                              <p></p>
                              <p class="text-center"> 로그인해주세요 </p>
                              </b-badge>
                            </h1>
                            <h5 class = "text-center">로그인 하지 않았습니다. 로그인을 해주세요</h5>
                              </div>





            
           <form @submit.prevent="login()">  <!-- login 부분 -->
                         <v-text-field
                         type="text"
                         placeholder="username"
                         v-model="user"

                         label="Email"
                         name="Email"
                         prepend-icon="email"
                         color="teal accent-3"
                         :rules="inputRules"
                         > </v-text-field>




                         <v-text-field
                         type="password"
                         placeholder="password" 
                         v-model="password"
                         
                         id="password"
                         label="Password"
                         name="Password"
                         prepend-icon="lock"
                         color="teal accent-3"
                         :rules="inputRules" ></v-text-field>

                </form>
                       </v-form>


                       <h3 class="text-center mt-2">Forget your password ? </h3>
                     </v-card-text>
                     <div class="text-center mt-3">
                       <v-btn variant="success" type="submit" rounded color="teal lighten-3" dark>SIGN IN</v-btn> 
                        <p v-if="error" class="error">Bad login information</p>

                       <v-btn rounded color="blue darken-1" text @click="dialog = false">Close</v-btn>
                     </div>
                     <h3 class="text-center mt-5"> </h3>
                    </v-col>
                    <v-col cols="12" md="4" class="teal lighten-3">
                      <v-card-text class="white--text mt-12">
                        <h1 class="text-center display-1">Hello, Friends !</h1>
                        <h5 class="text-center">Enter your personnel details and start journay with us</h5>
                      </v-card-text>

                      <div class="text-center">
                        <v-btn rounded outlined="" dark @click="step++">SIGN UP</v-btn>
                      </div> 
                      
                    </v-col>
                  </v-row>
               </v-window-item>
               <v-window-item :value="2">
                 <v-row class="">
                   <v-col cols="12" md="4" class="teal lighten-3">
                     <v-card-text class="white--text mt-12">
                       <h1 class="text-center display-1">Welcome Back! </h1>
                       <h5 class="text-center">To keep connected with us please login with your personnel info</h5>
                     </v-card-text>

                     <div class="text-center">
                       <v-btn rounded outlined dark @click="step--">SIGN IN</v-btn>
                     </div>

                     <div class="text-center"><v-card-text class="mt-2">
                       <v-btn rounded outlined dark @click="dialog = false">Close</v-btn>
                       </v-card-text>
                     </div>

                     
                   </v-col>

                   <v-col cols="12" md="8">
                     <v-card-text class="mt-12">
                       <h1 class="text-center display-2 teal--text text--lighten-3">Create Account</h1>
                      <div class="text-center mt-4">
                        <v-btn class="mx-2" fab-color="black" outlined>
                          <v-icon>fab fa-neos</v-icon>
                        </v-btn>
                        <v-btn class="mx-2" fab-color="black" outlined>
                         <v-icon>fab fa-google-plus-g</v-icon>
                       </v-btn>
                       <v-btn class="mx-2" fab-color="black" outlined>
                         <v-icon>fab fa-facebook-f</v-icon>
                       </v-btn>
                      </div>
                      <h4 class="text-center mt-4">Ensure your email for registration</h4>
                      <v-form>
                        <v-text-field
                        label="Name"
                        name="Name"
                        prepend-icon="person"
                        type="text"
                        color="teal lighten-3"/>

                        <v-text-field
                        label="Email"
                        name="Email"
                        prepend-icon="email"
                        type="text"
                        color="teal lighten-3" />

                        <v-text-field
                        label="Password"
                        name="Password"
                        prepend-icon="lock"
                        type="password"
                        color="teal lighten-3" />
                      </v-form>
                     <div class="text-center mt-3">
                      <v-btn rounded color="teal lighten-3" dark>SIGN UP</v-btn>
                     </div>
                     </v-card-text>
                   </v-col>
                 </v-row>
               </v-window-item>

               </v-window>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  
  </v-dialog>
  </v-row>
</template>


<script>

import axios from 'axios'

export default {
  name:'login',
  components:{

  },
  
  data: vm => {

    return {
                  loginSuccess: false,
                  loginError: false,
                  user: '',
                  password: '',
                  error: false
              },


              ({
      step : 1,
      dialog: false,
      title:'',
      content:'',
      due:null,
      date: new Date().toISOString().substr(0, 10),
      dateFormatted: vm.formatDate(new Date().toISOString().substr(0, 10)),
      menu1: false,
      inputRules: [
          v => v.length >= 7 || 'Minimum lenght is 7 charachters'
      ]
              })
      
    },

methods: {

     async login() {
                  try {
                      const result = await axios.get('/api/login', {
                          auth: {
                              username: this.user,
                              password: this.password
                          }
                      });
                      if (result.status === 200) {
                          this.loginSuccess = true
                      }
                  } catch (err) {
                      this.loginError = true;
                      throw new Error(err)
                  }
              }, // 로그인 정보 구현, 로그인 method 입니다.
              // auth는 axios 의 config 옵션. http 기본 인증(auth)이 사용되며, 자격 증명(credentials)을 제공함을 나타냄
              //기존의 Authorization 커스텀 헤더를 덮어쓰는 Authorization 헤더(header)를 설정한다.
              //username과 password를 가지고 있다


      formatDate (date) {
        if (!date) return null
        const [year, month, day] = date.split('-')
        return `${year}/${month}/${day}`
      },
      parseDate (date) {
        if (!date) return null
        const [year, month, day] = date.split('/')
        return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
      },
    },
    computed: {
      computedDateFormatted () {
        return this.formatDate(this.date)
      },
    },
    watch: {
      date () {
        this.dateFormatted = this.formatDate(this.date)
      },
    }, // 여기까지 숫자 ~이상 

    
    

 props: {
   
    source: String
  }
 
};



</script>
