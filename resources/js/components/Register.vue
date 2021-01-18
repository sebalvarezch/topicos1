<template>
      <div class="flex flex-wrap w-full justify-center items-center pt-52">
        <div class="flex flex-wrap max-w-xl">
            <div class="p-2 text-2xl text-gray-800 font-semibold"><h1>Registrar una cuenta</h1></div>
            <div class="p-2 w-full">
                <label class="w-full" for="name">Nombre</label>
                <span class="w-full text-red-500" v-if="errors.name">{{errors.name[0]}}</span>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Ingrese nombre" type="text" v-model="form.name" >
            </div>
            <div class="p-2 w-full">
                <label for="email">Correo electrónico</label>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Ingrese correo electrónico" type="email" v-model="form.email">
            </div>
            <div class="p-2 w-full">
                <label for="password">Contraseña</label>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Ingrese contraseña" type="password" v-model="form.password" name="password">
            </div>
            <div class="p-2 w-full">
                <label for="confirm_password">Confirme contraseña</label>
                <input class="w-full bg-gray-100 rounded border border-gray-400 focus:outline-none focus:border-indigo-500 text-base px-4 py-2" placeholder="Confirme contraseña" type="password" v-model="form.password_confirmation" name="password_confirmation">
            </div>
            <div class="p-2 w-full mt-4" align="center">
                <button @click.prevent="saveForm" type="submit" class="flex text-white bg-blue-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">Enviar formulario</button>
            </div>
        </div> 
    </div>
</template>
<script>
export default {
    data(){
        return{
            form:{
                name: '',
                email: '',
                password:'',
                password_confirmation:''
            },
            errors:[]
        }
    },
    methods:{
        saveForm(){
            axios.post('/api/register', this.form).then(() =>{
                console.log('saved');
            }).catch((error) =>{
                this.errors = error.response.data.errors;
            })
        }
    }
}
</script>