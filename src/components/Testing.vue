<template>
    <div class="testing">
        <div class="bd-example-row">
            <div class="bd-example">
                <div class="container">

                    <!-- Duplicate Normal -->
                    <!-- {{ Math.round( sampleData.PaymentDigests.length / 3) }} -->

                    <div 
                        class="staircase"
                        :class="isEven(i)"
                        v-for="(column, i) in chunkData"  
                        :key="i"  

                    >
                        <div class="row item-row">
                            <div class="item-col">
                                <div class="perspective">
                                    <div class="cube-extended"></div>
                                </div>​
                            </div>
                        </div>

                        <div 
                            class="row item-row"
                            v-for="(item, x) in column"
                            :key="x"
                        >
                            <div class="item-col">
                                <div class="perspective">
                                    <div class="cube" >{{ item.Name }}</div>
                                </div>​
                            </div>
                        </div>
                    </div>
                    
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            blockItems: 4,
            stairStatus: '',
            sampleData: {
                "PaymentDigests": [
                    {
                        "Id":3549478,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Anonymous",
                        "Amount":"00.00",
                        "Message":"Here's A Message",
                        "Created":"2020-10-07T07:14:10.8886913+00:00",
                        "LastUpdated":"2020-10-07T18:13:31.7584897+11:00"
                    },    
                    
                    {
                        "Id":3549476,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Josh Day",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":3549472,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 1",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {
                    "Id":35494743,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 2",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 3",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 4",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 5",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                                        {
                        "Id":3549478,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Anonymous",
                        "Amount":"00.00",
                        "Message":"Here's A Message",
                        "Created":"2020-10-07T07:14:10.8886913+00:00",
                        "LastUpdated":"2020-10-07T18:13:31.7584897+11:00"
                    },    
                    
                    {
                        "Id":3549476,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Josh Day",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":3549472,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 1",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {
                    "Id":35494743,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 2",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 3",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 4",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }, {

                    "Id":35494744,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 5",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },
                ],
                "ResultsReturned": 2,
                "PageNumber": 1,
                "TotalPages": 1
            }

        }
    },

    computed: {
        chunkData() {
            var values = Object.values(this.sampleData.PaymentDigests);
            var final = [];
            var counter = 0;
            var portion = {};

            for (var key in this.sampleData.PaymentDigests) {
                if (counter !== 0 && counter % this.blockItems === 0) {
                    final.push(portion);
                    portion = {};
                }
                portion[key] = values[counter];
                counter++
            }
            final.push(portion);

            return final;
        }
    },

    methods: {
        isEven(num) {
            if(num % 2 == 0) {
                return this.stairStatus = 'flipped'
            }
                return this.stairStatus = 'normal';

        },
    }
}
</script>

<style>

</style>