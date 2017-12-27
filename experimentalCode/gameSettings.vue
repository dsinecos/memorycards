<template>
    <div>
        <div class="difficulty-level">
            <game-settings-button v-for="item in difficultyLevel"></game-settings-button>
        </div>

        <div class="kind-of-tiles">
            <game-settings-button v-for="item in kindOfTiles"></game-settings-button>  
        </div>

        <div class="number-of-tiles">
            <game-settings-button v-for="item in kindOfTiles"></game-settings-button>
        </div>
    </div>
</template>

<script>
    import gameSettingsButton from './gameSettingsButton.vue';

    export default {
        data: function () {
            return {
                'difficultyLevel': ['Easy', 'Medium', 'Hard'],
                'kindOfTiles': ['Color', 'Image', 'Cards', 'Number'],
                'numberOfTiles': [5, 8, 10, 12, 15, 18, 20, 24]
            }
        },
        components: {
            'gameSettingsButton': gameSettingsButton
        }
    }

</script>

<style>
    .button {
        background-color: lightgrey;
        box-shadow: 1px 1px 1px grey;
        /* Green */
        border: 1px solid #aaa;
        border-radius: 12px;
        color: black;
        padding: 5px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 14px;
        margin: 2px 2px 12px 2px;
        cursor: pointer;
    }
</style>