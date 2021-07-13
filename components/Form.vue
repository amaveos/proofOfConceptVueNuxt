<template>
  <v-form class="form" v-model="valid">
    <v-container>
       
        <v-text-field class="input" v-model="email" :rules="emailRules" :counter="10" label="Usuario" required></v-text-field>

        <v-text-field class="input" v-model="password" type="password"  :rules="passwordRules" :counter="6" label="Contraseña" required ></v-text-field>

        <v-btn class="btn" block @click="logIn"> Entrar </v-btn>

        <div v-show="showDataForm">
            <p>Usuario: {{email}}</p>
            <p>Contraseña: {{password}}</p>
        </div>

    </v-container>
  </v-form>
</template>

<style scoped lang="scss">
    form{
        margin: 50px auto;
        width: 450px;

        .input{
            font-family: Arial, Helvetica, sans-serif;
        }

        .btn{
            background-color: #8bb124 !important;
            color: #fff;
            font-family: Arial, Helvetica, sans-serif;
            font-weight: 700;
            margin: 30px auto;
        }

        div{
            p{
                font-family: Arial, Helvetica, sans-serif;
                margin: 20px auto;
                text-align: center;
            }
        }
    }
</style>

<script>
  export default {
    data: () => ({
      valid: false,
      email: '',
      emailRules: [
        v => !!v || 'Debe ingresar un correo',
        v => /.+@.+/.test(v) || 'E-mail must be valid',
      ],
      passwordRules:[
        v => !!v || 'Debe ingresar una contraseña',
      ],
      showDataForm: false,
    }),
    methods: {
    logIn () {
          if(this.valid){
               this.showDataForm = true;
          }
      },
    },
  }
</script>