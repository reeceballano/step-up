<template>
    <div class="bd-example-row">
        <div class="bd-example">
            <div class="container">
                <div class="scroller">
                    <a @click="moveDown()" :href="`#stair-${currentStair}`"  class="text-white"><i class="fa fa-2x fa-arrow-down" style="color:white;" aria-hidden="true"></i></a>
                    <a @click="moveUp()" :href="`#stair-${currentStair}`" class="text-white"><i class="fa fa-2x fa-arrow-up" style="color:white;" aria-hidden="true"></i></a>
                </div>


                <div class="stair-container">
                    <div 
                        class="staircase"
                        :class="isEven(i)"
                        :key="i" 
                        :id="`stair-${i+1}`"
                        v-for="(column, i) in chunkData"  
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
                                    <div :style="{ 'background-color': setBackground(item.Amount) }" class="cube" ></div>
                                </div>​
                            </div>
                        </div>

                    </div>
                </div>
                    <pre>
                        {{ chunkData }}
                    </pre>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Working',
    components: {
    },

    data() {
        return {
            blockColor: '#6e68ff',
            blockItems: 3,
            stairStatus: '',
            stairItems: 1,
            currentStair: 1,
            sampleData: {
                "PaymentDigests": [
                    {
                        "Id":35494738,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Anonymous",
                        "Amount":"00.00",
                        "Message":"Here's A Message",
                        "Created":"2020-10-07T07:14:10.8886913+00:00",
                        "LastUpdated":"2020-10-07T18:13:31.7584897+11:00"
                    },    
                    
                    {
                        "Id":35492476,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Josh Day",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":35492472,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 1",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":35549471,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 2",
                        "Amount":"32.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":35494678,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Anonymous",
                        "Amount":"00.00",
                        "Message":"Here's A Message",
                        "Created":"2020-10-07T07:14:10.8886913+00:00",
                        "LastUpdated":"2020-10-07T18:13:31.7584897+11:00"
                    },    
                    
                    {
                        "Id":354945476,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Josh Day",
                        "Amount":"32.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":356749472,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 1",
                        "Amount":"00.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    },

                    {
                        "Id":354976471,
                        "Title":"",
                        "Description":"Tax Deductible Donation",
                        "Name":"Test name 2",
                        "Amount":"30.00",
                        "Message":"",
                        "Created":"2020-10-07T07:13:39.6523127+00:00",
                        "LastUpdated":"2020-10-07T18:13:00.4766103+11:00"
                    }
                ],
                "ResultsReturned": 2,
                "PageNumber": 1,
                "TotalPages": 1
            }
        }
    },

    computed: {
        totalBlocks() {
            return this.sampleData.PaymentDigests.length;
        },

        chunkData() {
            let values = Object.values(this.sampleData.PaymentDigests);
            let final = [];
            let counter = 0;
            let portion = {};

            for (let key in this.sampleData.PaymentDigests) {
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

    mounted() {
        let x = this.sampleData.PaymentDigests.sort((a, b) => parseFloat(b.Amount) - parseFloat(a.Amount));
        console.log(x)
    },

    methods: {
        isEven(num) {
            if(num % 2 == 0) {
                return this.stairStatus = 'flipped'
            }
                return this.stairStatus = 'normal';

        },

        moveDown() {
            console.log('down')
            this.sampleData.PaymentDigests.push([{},{},{},{},{}], [{},{},{},{},{}], [{},{},{},{},{}], [{},{},{},{},{}]);
            console.log(this.sampleData.PaymentDigests);

            this.currentStair++;
            this.stairItems++;
        },

        moveUp() {
            if(this.currentStair === 1) { return; }
            console.log('up');
            this.currentStair--;
            this.stairItems--;
        },

        
        setBackground(amount) {
            const amnt = parseFloat(amount);
            if(amnt > 0) {
                return this.blockColor;
            } else {
               return '#fff';
            }
        }
    }

}
</script>

<style lang="scss">
    .stair-container {
        padding-top: 60px;
        scroll-behavior: smooth;
        height: 550px;
        overflow: hidden;
    }

    .scroller {
        position: fixed;
        right: 15%;
        top: 30%;

        a {
            margin-right: 15px;
        }
    }
</style>
