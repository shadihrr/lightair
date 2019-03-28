<template>
    <div>
        <ul>
            <li v-bind:key="report.id" v-for="report in reports">
                <report v-bind:report="report"/>
            </li>
        </ul>
    </div>
</template>

<script>
    import report from "./report"

    export default {
        name: 'Report',
        components: {report},
        props: ["reports"]
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        height: 40px;
        background: #ffe07b;
        border: solid 1px gray;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
