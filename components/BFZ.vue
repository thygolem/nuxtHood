<template>
<div>
    <h1> taskS </h1>
    <h2> Sistemas de automatización de tareas </h2>
    <h3> Entornos: 
            <h4> 
            <ul>Logístico</ul>
            <ul>Sanitario</ul>
            <ul>Hostelería</ul>
            </h4>
    </h3>
    <hr>

    <hr>

    <br>
    <table>
        <tr>
            <th> ALIAS </th>
            <th> ACTIVE </th>
            <th> TAG </th>
            <th> Building </th>
            <th> Floor </th>
            <th> Zone: <span style="color: green"> click to locate this item </span> </th>
        </tr>
        <tr v-for="device in devices" :key="device">
            <td> {{ device.alias }} </td>
            <td> {{ device.active }} </td>
            <td> {{ device.tag }} </td>
            <td> <button> {{ device.b }} </button> </td>
            <td> <button> {{ device.f }} </button> </td>
            <td> <button style="color: green"> {{ device.z }} </button>  </td>
        </tr>
    </table>
    <br>
    <table>
        <td> ALIAS <input v-model="newDevice.alias"> </td>
        <td> MAC:ADDRESS = TOPIC: <input v-model="newDevice.topic"> </td>
        <td> TAG <input v-model="newDevice.tag"> </td>
        <h3> <button @click="addDevice()"> AÑADIR </button></h3>
    </table>
    <hr>
</div>
</template>

<script>
export default{
    props: {

    },
    data() {
        return {
            devices:[],
            newDevice: {
                alias: '',
                b: '',
                f: '',
                z: '',
                active: '',
                topic: '',
                tag:'',
            }, 
        }
    },
    created() {

    },
    mounted() {
        this.getDevices();
    },
    methods: {
        addDevice() {
            //...TO API
            this.devices.push(JSON.parse(JSON.stringify(this.newDevice)));
        },
        getDevices() {
            //...FROM API
            var response = [
                {
                    alias: "HUMANO",
                    // B, F, Z y active se recogen de la DB
                    // Es una información gestionada con Django donde podremos añadir mayor información
                    // Sería deseable poder     
                    b: "A",
                    f: "B",
                    z: "C",
                    active: false,
                    tag: "#electromecanico",
                    topic: "AA:BB:CC"
                },
                {
                    alias: "ROBOT",    
                    b: "X",
                    f: "Y",
                    z: "Z",
                    active: true,
                    tag: "#asistente",
                    topic: "XX:YY:ZZ"
                }
            ];
            this.devices = response;
        }
    },
}
</script>

<style>

</style>
