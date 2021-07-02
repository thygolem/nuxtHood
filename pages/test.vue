<template>
    <div style="padding:15px">
        <br>
        <h2>
        NEAR DEVICES: {{ devices.length }}
        </h2>
        <table>
            <tr>
                <th>Name</th>
                <th>Id</th>
                <th> TEMP</th>
            </tr>

            <tr v-for="device in devices" :key="device">
                <td> {{ device.name.toUpperCase() }} {{ device.status }} </td>
                <td> {{ device.id }} </td>
                <td> {{ device.value }}  ºC</td>
                <td> <button> INDOOR TRACKING </button></td>
            </tr>
        </table>
        <br>
        <hr>
        <h4>
        Nombre: <span style="color: green"> {{newDevice.name}}</span> <br>
        Id: <span style="color: green">{{newDevice.id}}</span><br>
        Value: <span style="color: green">{{newDevice.value}}</span><br><br>
        <button @click="addDevice()">LISTO</button>
        </h4>
        <hr>
        <br>
        <h3> NUEVOS DISPOSITIVOS: </h3>
        <h5>NAME <br><input v-model="newDevice.name"></h5>
        <h5>ID<br><input v-model="newDevice.id"></h5>
        <h5>VALUE<br><input v-model="newDevice.value"></h5>

    </div>
</template>


<script>
    export default{
        data() {
            return {
                devices:[],
                newDevice: {
                    name: '',
                    id: '',
                    value: '',
                }
            }
        },
        created() {
            console.log(Date.now())
        },
        mounted() {
            this.getDevices();

        },

        methods: {
            addDevice() {
                //...API
                //... Solución a "Reactividad no deseada", capítulo .82 de Ioticos
                this.devices.push(JSON.parse(JSON.stringify(this.newDevice)));
            },
            getDevices() {
                //...API
                var response = [
                    {
                        name: "UNO",
                        id: "6666",
                        value: 7,
                        status: "&#9800;"
                    },
                    {
                        name: "DOS",
                        id: "7777",
                        value: 7,
                        status: "&#9810;"
                    }
                ];
                this.devices = response;
            }
        } 
    }
</script>


<style>
    table, th, td {
        border-collapse: collapse;
        border: 3px solid red;
        padding:10px;
    }
    h5 {
        border: 0.5px solid green;
        padding:10px;
    }
    h4 {
        border: 0.2px solid blue;
        padding:10px;
    }
</style>

