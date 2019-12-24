<template>
    <div id="tipCalc">
        <v-container  fluid>
        <v-form >  
                <v-row
                justify="center">
                    <v-col cols="6"
                    md="3">
                        <h2>Tip Calculator</h2>
                    </v-col>
                    <v-col cols="6" class="alert">
                        <p>{{alert}}</p>
                    </v-col>
                </v-row>
            <v-row 
            justify="center">
                <v-col
                cols=12
                md="12"
                >
                    <div class="results">
                        <p>
                            {{results || "$0.00"}}
                        </p> 
                    </div>
                </v-col>
            </v-row>
            <v-row justify="center">
                <v-col
                cols=12
                md="12">
                    <v-text-field
                    type="number"
                    class="remove"
                    v-model="cost"
                    label="Meal Cost"
                    filled
                    prepend-inner-icon="attach_money"
                    onkeypress="isInputNumber(event)"
                    
                    >
                    </v-text-field>
                </v-col>
                <v-col
                cols=12
                md="12">
                    <v-select
                        v-model="inputPeople"
                        :items="people"
                        item-text="title"
                        item-value="value"
                        label="Number of People"
                        
                        filled
                        prepend-inner-icon="people">
                        >
                    </v-select>
                </v-col>
                <v-col
                cols=12
                md="12">
                    <v-select
                        v-model="inputPercent"
                        :items="percent"
                        label="Tip Percent"
                        item-text="title"
                        item-value="value"
                        filled>
                    </v-select>
                </v-col> 
            </v-row>
            <v-row 
            justify="center">
                <v-col class="text-center"
                cols=12
                md="12">
                    <v-btn block dark x-large @click="tipCalc">Calculate</v-btn>
                </v-col>
            </v-row>
            
        </v-form>
        </v-container>
    </div>
</template>

<script>

export default {
    data() {
        return{
            results: '',
            cost: null,
            inputPercent: '',
            inputPeople: '',
            alert: '',
            people: [
                {title: "1", value: 1},
                {title: "2", value: 2},
                {title: "3", value: 3},
                {title: "4", value: 4},
                {title: "5", value: 5},
                {title: "6", value: 6},
                {title: "7", value: 7},
                {title: "8", value: 8},
                {title: "9", value: 9},
            ],
            percent: [
                {title: '5%', value: .05},
                {title: '10%', value: .10},
                {title: '15%', value: .15},
                {title: '20%', value: .20},
                {title: '25%', value: .25},
                {title: '30%', value: .3},
                {title: '35%', value: .35},
                {title: '40%', value: .4},
            ],
        }
    },
    methods: {
        tipCalc() {
            if(this.cost == null) {
                this.results = "$0.00"
                
            }
            else if (this.cost <= 0) {
                this.alert = "Please enter a number above 0";
                this.results = "ERROR"
            
            } else {
                let tipResults = (this.cost * this.inputPercent) / this.inputPeople;  
                let resultsRounded = tipResults.toFixed(2);
                this.results = "$" + resultsRounded;
                this.alert= "";
            }
        },

        isInputNumber(evt) {
            var ch = String.fromCharCode(evt.which);
            if(!(/[0-9]/.test(ch))){
                evt.preventDefault();
            }

        }
    }
}
</script>

<style lang="scss" scoped>



    .results {
        height: 100px;
        width: 100%;
        background: lightgray;
        border-radius: 5px;
        font-size: 50px;
        text-align: center;
        margin-bottom: 20px;
        p {
            padding: 10px;
        }
    }
    #tipCalc {
        margin-top: 40px;
        padding-bottom: 1em;
        max-width: 400px;
        margin-left: auto;
        margin-right: auto;
        background: white;
        border-radius: 10px;
        box-shadow: 4px 6px 9px;
    }
     
        .remove::-webkit-inner-spin-button, 
        .remove::-webkit-outer-spin-button { 
        -webkit-appearance: none; 
        margin: 0; 
    }

    .alert {
        color: red;
        font-size: 12px;
        top: 5px;
    }

    

    
</style>
