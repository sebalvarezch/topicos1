<template>
    <div>

        <header>
            <sidebar>
             <div>
              <div class="dropdown inline-block relative">
                <button class="bg-gray-300 text-gray-700 font-semibold py-2 px-4 rounded inline-flex items-center">
                  <span class="mr-1">Sidebar</span>
                  <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/> </svg>
                </button>
                <ul class="dropdown-menu absolute hidden text-gray-700 pt-1">
                  <li class=""><img style="margin-left: 5px; width: 20px; height: 20px; margin-top: 10px; margin-right: 5px" :src="require('./assets/admin.png')" align="left" /><a class="rounded-t bg-gray-200 hover:bg-gray-400 py-2 px-4 block whitespace-no-wrap" href="#">Perfil Administrador</a> </li>
                  <li class=""><img style="margin-left: 8px; width: 20px; height: 20px; margin-right: 5px; margin-top: 10px" :src="require('./assets/descarga.png')" align="left" /><a class="bg-gray-200 hover:bg-gray-400 py-2 px-4 block whitespace-no-wrap" href="#" style="">Componentes <br> Web</a></li>
                  <li class=""><a class="rounded-b bg-gray-200 hover:bg-gray-400 py-2 px-4 block whitespace-no-wrap" href="#"><img style="margin-left: -8px;width: 20px; height: 20px;" :src="require('./assets/multimedia.png')" align="left" />Galería de Vídeos,<br> Mensajes</a></li>
                </ul>
              </div>
            </div>
         </sidebar>   
            <div align="right">
                Dashboard
            </div> 

        </header>
        
        
         

        <div v-if="user" align="right">
        Name: {{user.name}} <br>
        Email: {{user.email}}<br><br>
       
        </div>

        <content>
            <div align="right">
                <button @click.prevent="logout" class="flex text-white bg-blue-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg justify-left">Logout</button>
            </div>
             
            <div align="center">
                <h1 style="margin-top: 100px; font-size: 50px;">Vista Administrador</h1>
            </div>
        </content>

       
    </div>
</template>
<script>
export default {
    data(){
        return{
            user: null
        }
    },
    methods:{
        logout(){
            axios.post('/api/logout').then(()=>{
                this.$router.push({ name: "Home"})
            })
        }
    },
    mounted(){
        axios.get('/api/user').then((res)=>{
            this.user = res.data
        })
    }
}
</script>

<style type="text/css">
    .dropdown:hover .dropdown-menu {
  display: block;
}
</style>