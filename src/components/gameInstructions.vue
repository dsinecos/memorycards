<template>
    <div >
        <h3>
            <span class="glyphicon glyphicon-chevron-down icon" aria-hidden="true" @click="toggleInstructionDisplay"></span> Instructions
        </h3>
        <div v-if="displayInstructionStatus" class="instructions">
            <ol>
                <li>
                    <p>Click a Tile to reveal the Image (or Color) behind it</p>
                </li>
                <li>
                    <p>Click two tiles consecutively with the same Image (or Color) to eliminate them from the board</p>
                </li>
                <li>
                    <p>Clear all the tiles in as few clicks and as quickly to score the maximum</p>
                </li>
            </ol>
        </div>
    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                displayInstructionStatus: true
            }
        },
        methods: {
            toggleInstructionDisplay: function () {
                this.displayInstructionStatus = !this.displayInstructionStatus;
            }

        }
    }
</script>

<style>
    .container {
        /* margin: auto; */
        /* border: 2px solid black; */
        padding: 5px;
        padding-bottom: 10px;
    }

    .instructions {
        border: 2px solid #eee;
        padding: 5px;
        display: inline-block;
    }

    .icon {
        cursor: pointer;
    }
</style>