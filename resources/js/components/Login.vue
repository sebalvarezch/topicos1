<template>
     <div class="flex flex-wrap w-full justify-center items-center pt-52">
        <div class="flex flex-wrap max-w-xl">
            <div class="p-2 text-2xl text-gray-800 font-semibold"><h1>Inicia sesión</h1></div>
            <div class="p-2 w-full">
                <label for="email">Correo electrónico</label>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Ingrese correo electrónico" type="email" v-model="form.email">
            </div>
            <div class="p-2 w-full">
                <label for="password">Contraseña</label>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Ingrese contraseña" type="password" v-model="form.password" name="password">
            </div>
            <div class="p-2 w-full mt-4" align="center">
                <button @click.prevent="loginUser" type="submit" class="flex text-white bg-blue-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Iniciar Sesión</button>
            </div>
        </div> 
    </div>
</template>
<script>
export default {
    data(){
        return{
            form:{
                email: '',
                password: ''
            },
            errors: []
        }
    },
    methods:{
         loginUser(){
             axios.post('/api/login', this.form).then(() =>{
                 this.$router.push({ name: "Dashboard"}); 
             }).catch((error) =>{
         this.errors = error.response.data.errors;
            })
         }
    }
}
</script>