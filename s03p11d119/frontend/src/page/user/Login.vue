<template>
    <div class="user" id="login">
        <div class="wrapC table">
            <div class="middle">
                <h1>SS_log</h1>
                <div class="input-wrap">
                    <input v-model="email"
                        id="email" 
                        placeholder="이메일을 입력해주세요"
                        type="text"/>
                </div>
                <div class="input-wrap">
                    <input v-model="password" type="password"
                        id="password"
                        placeholder="영문, 숫자 혼용 8자 이상"/>
                </div>
                <button class="btn btn--back btn--login"  @click="login">
                    로그인 하기
                </button>
                <div class="add-option">
                    <div class="wrap">
                        <p>아직 회원이 아니신가요?</p>
                        <router-link v-bind:to="{name:constants.URL_TYPE.USER.JOIN}" class="btn--text">
                            회원가입
                        </router-link>
                    </div>

                </div>
            </div>
            
        </div>

    </div>
</template>

<script>
    import '../../assets/css/user.scss'
    import constants from '../../lib/constants'
    import axios from 'axios'

    export default {
        data: () => {
            return {
                constants,
                email: '',
                password: '',

            }
        },
        components: {
        },
        created(){
        },
        watch: {
        },
        methods: {
            login(){
            console.log("dd");
            console.log(email);
            console.log(password);
                //백앤드와 로그인 통신하는 부분
            axios.get('http://localhost:8080/account/login', {
                params:{
                    email:this.email, password:this.password}
            })
            .then(res => {
                console.log("login success");
            })
            .catch(res => {
                console.log("login fail");
            });

            }
        }

    }

</script>