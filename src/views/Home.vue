<template>
  <div id="app">
    <login></login>
    <!--<AddReport v-on:add-report="addReport"></AddReport>-->
    <!--<Reports v-bind:reports="reports" v-on:del-report="deleteReport"></Reports>-->
  </div>
</template>

<script>
    import Reports from "../components/Reports"
    import AddReport from "../components/AddReport"
    import login from "../components/login"
    export default {
        name: 'Home',
        components: {
            Reports, AddReport, login

        },
        data(){
            return{
                reports:[{id:1,desc:"", charity:"", date:"", skipped:true}]
            }
        },
        methods:{
            deleteReport(id){
                console.log(id)
                this.reports = this.reports.filter(report => report.id !== id);
            },
            addReport(report){
                console.log(report)
                this.reports.push(report);
            }
        }
    }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
