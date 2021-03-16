<template>
    <div class="container">
        <form>
            <div class="row">
                <div class="col-lg-12 col-md-6 col-xs-12">
                    <h1>{{title}}</h1><hr>
                    <div class="form-group">
                        <label for="nombre">Nombre:</label>
                        <input type="text" id="nombre" class="form-control" v-model="datosPersona.nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="email">E-mail:</label>
                        <input type="text" id="email" class="form-control" v-model="datosPersona.email">
                    </div>
                    <div>
                        <label for="mensaje">Mensaje</label>
                        <textarea id="mensaje" cols="70" rows="5" v-model="mensaje"></textarea>
                    </div>
                </div>
                <!-- Checkbox -->
                <div class="row">
                    <div class="col-lg-12 col-md-6 col-xs-12">
                        <div class="form-group">
                            <label for="caminar">
                                <input type="checkbox" id="caminar" value="caminar" v-model="opcionCheck"> Caminar
                            </label>&nbsp;&nbsp;
                            <label for="bailar">
                                <input type="checkbox" id="bailar" value="bailar" v-model="opcionCheck"> Bailar
                            </label>&nbsp;&nbsp;
                            <label for="comer">
                                <input type="checkbox" id="comer" value="comer" v-model="opcionCheck"> Comer
                            </label>
                        </div>
                    </div>
                </div>
                <!-- RadioButton -->
                <div class="row">
                    <div class="col-lg-12 col-md-6 col-xs-12">
                        <div class="form-group">
                            <label for="masculino">
                                <input type="radio" id="masculino" value="M" v-model="genero"> Masculino
                            </label>&nbsp;&nbsp;
                            <label for="femenino">
                                <input type="radio" id="femenino" value="F" v-model="genero"> Femenino
                            </label>
                        </div>
                    </div>
                </div>

                <!-- ComboBox -->
                <div class="row">
                    <div class="col-lg-12 col-md-6 col-xs-12">
                        <label for="horario">Horario </label>
                        <select id="horario" class="form-control" v-model="horario">
                            <option v-for="item in datosHorario" :key="item" :selected="item =='Tarde'">{{item}}</option>
                        </select>
                    </div>
                </div>

                <div class="row">
                    <div class="col-lg-12 col-md-6 col-xs-12"><br>
                        <button class="btn btn-primary" @click.prevent="enviar">Submit</button>
                    </div>
                </div>
            </div>
        </form>

        <div class="row" v-if="enviado">
            <div class="row mt-4">
                <div class="col-lg-12">
                    <div class="panel panel-default">
                        <div class="panel-heading">
                            <h2>Datos Ingresados</h2>
                        </div>
                        <div class="panel-body">
                            <p><strong>Nombre:</strong> {{datosPersona.nombre}}</p>
                            <p>Email: {{datosPersona.email}}</p>
                            <p style="white-space:pre">Mensaje:<br> {{mensaje}}</p>
                            
                            <p>Opcion de check</p>
                            <ul>
                                <li v-for="op in opcionCheck" :key=op>{{op}}</li>
                            </ul>
                            <p>Genero: {{genero}}</p>
                            <p>Horario: {{horario}}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name:'Formulario',
    data(){
        return {
            title:'Formulario de contacto',
            // Agrupar datos a nivel de objeto
            datosPersona:{
                nombre: '',
                email:''
            },
            mensaje:'',
            opcionCheck:[],
            genero:'M',//M por defecto
            horario:'',
            datosHorario:['Mañana','Tarde','Noche'],
            enviado:false

        }
    },
    methods:{
        enviar(){
            this.enviado= !this.enviado
        }
    }
}
</script>

<style>

</style>