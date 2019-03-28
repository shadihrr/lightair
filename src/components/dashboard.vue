<template>
    <div >
        <AddReport v-on:add-report="addReport" />

        <Reports v-bind:reports="reports" v-on:del-report="deleteReport"></Reports>
    </div>
</template>

<script>
    import axios from 'axios';
    import Reports from "../components/Reports"
    import AddReport from '../components/AddReport';

    export default {
        name: "dashboard",
        components: {
            Reports, AddReport

        },
        data(){
            return{
                reports: []
            }
        },
        methods:{
            deleteReport(id){
                console.log(id)
                this.reports = this.reports.filter(report => report.id !== id);
            },
            addReport(newReport) {
                const { desc, charity, skipped } = newReport;
                var token = localStorage.getItem('jwt')
                axios.post('http://127.0.0.1:8000/api/v1/reports/store?token='+token, {
                    desc,
                    charity, skipped
                })
                    .then(res => {
                        console.log(res)
                        this.reports = [...this.reports, res.data.data.report]
                        console.log(this.reports)
                    })
                    .catch(err => console.log(err));
            }, getReports()  {
                var token = localStorage.getItem('jwt')
                axios.get('http://127.0.0.1:8000/api/v1/reports?token='+token)
                    .then(res => {
                        console.log(res)
                       this.reports = res.data.data
                    }).catch(err => console.log(err));
            }
        },
        created(){
            this.getReports()
        }
    }
</script>

<style scoped>

</style>