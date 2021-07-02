<template>
<div>
    <h1> taskS </h1>
    <h2> Sistemas de automatización de tareas </h2>
    <h3> Entornos: </h3>
    <h4> 
            <ul>Logístico</ul>
            <ul>Sanitario</ul>
            <ul>Hostelería</ul>
    </h4>
    <hr>
    <table>
        <td> NAME <input type="text"> </td>
        <td> ESPID: <input type="text"> </td>
        <td> Type <input type="text"> </td>
        <h3> <button @click="addDevice()"> AÑADIR </button></h3>
    </table>
    <hr>
    <br>
    <table>
        <tr>
            <th> NAME </th>
            <th> ACTIVE </th>
            <th> Building </th>
            <th> Floor </th>
            <th> Zone </th>
        </tr>
        <tr v-for="device in devices" :key="device">
            <td> UNO </td>
            <td> {{ device.active }} </td>
            <td> {{ device.b }} </td>
            <td> {{ device.f }} </td>
            <td> {{ device.z }} </td>
            <td> <button onclick="window.location.href='/test'"> LOCATE {{ device.position }} </button> </td>
        </tr>
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
                b: '',
                f: '',
                z: '',
                active: '',
                position: '',
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
                    b: "A",
                    f: "B",
                    z: "C",
                    active: false,
                    position: "ESPID:f",
                },
                {
                    b: "X",
                    f: "Y",
                    z: "Z",
                    active: true,
                    position: "ESPID:a",

                }
            ];
            this.devices = response;
        }
    },
}
</script>

<style>

</style>
