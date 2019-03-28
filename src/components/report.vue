<template>
    <div class="item">
        <div v-bind:class="{'is-skipped':report.skipped}">
            Description: {{report.name}} - <span v-if="report.charity">I donated for {{report.charity}}</span> - on {{report.date}}
        </div>
    </div>
</template>

<script>
    export default {
        name: "report",
        props:["report"],
        methods:{
            skipped(){
                console.log("salam");
                this.report.skipped = !this.report.skipped;
            }
        }
    }
</script>

<style scoped>
    .is-skipped{
        background: #4CAF50;
        height: 100%;
        line-height: 2.5em;
        color: #dadee6;
    }
    .item{
        text-align: left;
        height: 40px;
        line-height: 2.5em;
    }

</style>