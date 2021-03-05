<template>
    
    <div>

        <div v-if="loading">
            <img src="https://res.cloudinary.com/adenike/image/upload/v1606839887/Spinner-transparent-bg_neytod.svg" alt="loader">
        </div>
        
        <div v-else>
            <ul class="list-unstyled my-5">
                <li class="my-2"><span class="font-weight-bold">Total Samples Tested: </span>{{ results.totalSamplesTested }}</li>
                <li class="my-2"><span class="font-weight-bold">Total Confirmed Cases: </span>{{ results.totalConfirmedCases }}</li>
                <li class="my-2"><span class="font-weight-bold">Total Active Cases: </span>{{ results.totalActiveCases }}</li>
                <li class="my-2"><span class="font-weight-bold">Total Discharged: </span>{{ results.discharged }}</li>
                <li class="my-2"><span class="font-weight-bold">Total Death: </span>{{ results.death }}</li>
                
            </ul>

            <table class="table table-dark table-striped table-hover table-responsive-sm">
                <thead>
                    <tr>
                    <th scope="col">#</th>
                    <th scope="col">State</th>
                    <th scope="col">Confirmed Cases</th>
                    <th scope="col">Cases on Admission</th>
                    <th scope="col">Discharged</th>
                    <th scope="col">Death</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="(state, index) in states" :key="state.id">
                    <th scope="col">{{ index + 1 }}</th>
                    <th scope="col">{{ state.state }}</th>
                    <th scope="col">{{ state.confirmedCases }}</th>
                    <th scope="col">{{ state.casesOnAdmission }}</th>
                    <th scope="col">{{ state.discharged }}</th>
                    <th scope="col">{{ state.death }}</th>
                    </tr>
                </tbody>
            </table>
        </div> 

        <small>{{ error }}</small>       
    </div>
</template>

<script>
import axios from 'axios'

export default {
    name: "Tracker",
    
    data () {
        return {
            fields: ['#', 'States', 'Confirmed Cases', 'Cases on Admission', 'Discharged', 'Death'],
            loading: {type: Boolean},
            results: null,
            states: '',
            url: 'https://covidnigeria.herokuapp.com/api', 
            error: null,         
        }
    },
    mounted() {
        this.getTracker(this.url)
    },

    methods: {
        async getTracker(api) {
            try {
                this.loading; 
                axios
                .get(api)
                .then(res => {
                    this.loading = false
                    this.results = res.data.data;
                    this.states = this.results.states;
                })      
            } catch (error) {
                console.log(error)
                this.loading = false
                this.error = error
            }
        }
    },
}
</script>

<style scoped>

* {
    font-size: 18px;
}

li, li span {
    font-size: 1.3rem;
}

</style>