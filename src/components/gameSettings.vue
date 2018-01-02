<template>
    <div>
        <h3>
            <span class="glyphicon glyphicon-chevron-down" aria-hidden="true" @click="toggleDisplay"></span> Game Settings </h3>

        <div v-if="displayGameSettings">
            <div class="game-settings-item">
                <p>Difficulty Level</p>
                <game-button v-for="item in difficultyLevel" :key="item.buttonID" :buttonText="item.buttonText" buttonType="difficultyLevel"
                    :isActive="item.isActive" @gameSettingButtonClicked="buttonClicked"  :isDisabled="item.isDisabled"></game-button>
            </div>

            <div class="game-settings-item">
                <p>Background for tiles</p>
                <game-button v-for="item in cardBackground" :key="item.buttonID" :buttonText="item.buttonText" buttonType="cardBackground"
                    :isActive="item.isActive" @gameSettingButtonClicked="buttonClicked" :isDisabled="item.isDisabled"></game-button>
            </div>

            <div class="game-settings-item">
                <p>Number of unique tiles</p>
                <game-button v-for="item in numOfUniqueCards" :key="item.buttonID" :buttonText="item.buttonText" buttonType="numOfUniqueCards"
                    :isActive="item.isActive" @gameSettingButtonClicked="buttonClicked" :isDisabled="item.isDisabled"></game-button>
            </div>

        </div>

        <div>
            <button @click="startGame">Start Game</button>
        </div>

    </div>
</template>

<script>
    import gameButton from './gameButton.vue';
    import { eventBus } from '../main';

    export default {
        data: function () {
            return {
                displayGameSettings: true,
                'gameSettings': {
                    'difficultyLevel': "Easy",
                    'cardBackground': "Color",
                    'numOfUniqueCards': 10,
                },
                'difficultyLevel': [
                    {
                        'buttonID': 1,
                        'buttonText': 'Easy',
                        'isActive': false,
                        'isDisabled': false
                    },
                    {
                        'buttonID': 2,
                        'buttonText': 'Medium',
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 3,
                        'buttonText': 'Hard',
                        'isActive': false,
                        'isDisabled': true
                    }
                ],
                'cardBackground': [
                    {
                        'buttonID': 1,
                        'buttonText': 'Color',
                        'isActive': false
                    },
                    {
                        'buttonID': 2,
                        'buttonText': 'Image',
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 3,
                        'buttonText': 'Number',
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 4,
                        'buttonText': 'Cards',
                        'isActive': false,
                        'isDisabled': true
                    },
                ],
                'numOfUniqueCards': [
                    {
                        'buttonID': 1,
                        'buttonText': 5,
                        'isActive': false
                    },
                    {
                        'buttonID': 2,
                        'buttonText': 8,
                        'isActive': false
                    },
                    {
                        'buttonID': 3,
                        'buttonText': 10,
                        'isActive': false
                    },
                    {
                        'buttonID': 4,
                        'buttonText': 12,
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 5,
                        'buttonText': 15,
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 6,
                        'buttonText': 18,
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 7,
                        'buttonText': 20,
                        'isActive': false,
                        'isDisabled': true
                    },
                    {
                        'buttonID': 8,
                        'buttonText': 24,
                        'isActive': false,
                        'isDisabled': true
                    },
                ]
            }
        },
        components: {
            'gameButton': gameButton
        },
        methods: {
            toggleDisplay: function () {
                console.log("toggleDisplay function executed");
                this.displayGameSettings = !this.displayGameSettings;
            },
            buttonClicked: function (buttonType, buttonText) {

                this.gameSettings[buttonType] = buttonText;

                if (this.gameSettings.cardBackground !== 'Color') {
                    // console.log("Check inside if ");
                    this.difficultyLevel.forEach(function (item) {
                        item.isDisabled = true;
                        item.isActive = false;
                    });
                    this.gameSettings.difficultyLevel = "";

                } else if (this.gameSettings.cardBackground === 'Color') {
                    // console.log("Check inside if else ");
                    this.difficultyLevel.forEach(function (item) {
                        item.isDisabled = false;
                    });
                }

                this[buttonType].forEach(function (item) {
                    if (item.buttonText === buttonText) {
                        item.isActive = true;
                    } else {
                        item.isActive = false;
                    }
                });


            },
            startGame: function () {
                console.log("To start game");
                console.log("Game Settings");
                console.log(JSON.stringify(this.gameSettings, null, "  "));

                this.$store.state.numOfCardsBeginning = this.gameSettings.numOfUniqueCards;
                this.$store.state.numOfCardsCurrent = this.gameSettings.numOfUniqueCards;
                eventBus.$emit('setupNewGame');
            }
        }
    }

</script>

<style>
    .game-settings-item {
        display: inline-block;
        margin: 2px;
        border: 2px solid #eee;
        padding: 5px;
    }

    .game-settings-item p {
        color: #555;
        font-weight: bold;
    }
</style>