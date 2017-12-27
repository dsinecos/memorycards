<template>
    <div>

        <h3>Game Stats</h3>

        <div class="game-stats-component">
            <h3 id="timer">{{ hours }}
                <span class="timer-text">Hours</span> {{ minutes }}
                <span class="timer-text">Minutes</span> {{ seconds }}
                <span class="timer-text">Seconds</span>
            </h3>
            <!-- <br>
            <button @click="start">Start</button>
            <button @click="stop">Stop</button>
            <button @click="reset">Reset</button> -->
        </div>

        <div class="game-stats-component">
            <h4> # Clicks : {{ numOfClicks }}</h4>
            <h4> Score : {{ score }}</h4>
        </div>


    </div>

</template>

<script>
    export default {
        data: function () {
            return {
                startTime: 0,
                currentTime: 0,
                interval: null,
                millisecondsWhenPaused: 0
            }
        },
        computed: {
            numOfClicks: function () {
                return this.$store.state.numOfClicks;
            },
            score: function () {
                return this.$store.state.numOfCardsBeginning - this.$store.state.numOfCardsCurrent;
            },
            time: function () {
                return this.hours + ':' + this.minutes + ':' + this.seconds;
            },
            milliseconds: function () {
                return this.currentTime - this.startTime;
            },
            hours: function () {
                var lapsed = this.milliseconds;
                var hrs = Math.floor((lapsed / 1000 / 60 / 60));
                return hrs >= 10 ? hrs : '0' + hrs;
            },
            minutes: function () {
                var lapsed = this.milliseconds;
                var min = Math.floor((lapsed / 1000 / 60) % 60);
                return min >= 10 ? min : '0' + min;
            },
            seconds: function () {
                var lapsed = this.milliseconds;
                var sec = Math.ceil((lapsed / 1000) % 60);
                return sec >= 10 ? sec : '0' + sec;
            }
        },
        methods: {
            reset: function () {
                // this.state = "started";
                this.startTime = Date.now();
                this.currentTime = Date.now();
            },
            start: function () {
                this.startTime = Date.now();
                this.currentTime = Date.now();
                this.interval = setInterval(this.updateCurrentTime, 1000);
            },
            stop: function () {
                clearInterval(this.interval);
                this.startTime = 0;
                this.currentTime = 0;
            },
            updateCurrentTime: function () {
                this.currentTime = Date.now();
            }
        },
        watch: {
            numOfClicks: function(newVal, oldVal) {
                // console.log("Detected");
                // console.log("Oldval : " + oldVal);
                // console.log("NewVal : " + newVal);
                if(newVal === 1) {
                    this.start();
                }
                // this.start();
            },
            score: function(newVal) {
                // console.log("Detected Score");
                if(newVal === this.$store.state.numOfCardsBeginning) {
                    this.stop();
                }
            }
        }
    }
</script>

<style>
    #timer {
        background-color: #34495E;
        color: #ECF0F1;
        display: inline-block;
        padding: 10px;
        border: 2px groove white;
    }

    .timer-text {
        color: #1ABB9A;
        font-size: 12px;
    }

    .game-stats-component {
        display: inline-block;
        vertical-align: top;
        margin: 5px;
        padding: 5px;
        /* border: 2px groove grey; */
    }
</style>