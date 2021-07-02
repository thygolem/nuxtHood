<template>
    <div>
        <h1>  </h1>
        <h2> {{count}} </h2>
        <h3>  </h3>
        <h4>  </h4>
        <table>
            <tr>
                <th>  </th>
                <th>  </th>
                <th>  </th>
            </tr>
            <tr>
                <td>  </td>
                <td>  </td>
                <td>  </td>
                <td>  </td>
            </tr>
        </table>
    </div>
</template>

<script>
export default{
    props:{
        initialValue: {
            required: true,
            type: Number,
            default: 10,
            description: 'Please, write the main value',
        },
        delay: {
            default: 1000
        }
    },
    data() {
        return {
            count: 10,
        }
    },
    created() {

    },
    mounted() {
        this.count = this.initialValue;
        this.startCountDown();
    },
    methods: {
        startCountDown() { 
            setTimeout(() => {
                this.count--;
                this.startCountDown();
            }, this.delay);
        } 
    },
}
</script>
