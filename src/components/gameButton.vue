<template>

        <button @click="buttonClicked" class="game-setting-button" :class="{ 'button-is-active': isActive, disabledButton: isDisabled }">{{ buttonText }}</button>
    
    </template>
    
    <script>
        export default {
            props: ['buttonText','buttonType','isActive','isDisabled'],
            // data: function () {
            //     return {
            //         buttonText: "John Doe",
            //         buttonType: "",
            //         isActive: true
            //     }
            // }
            methods: {
                buttonClicked: function() {
                    //Throw an event with the needed arguments
                    this.$emit('gameSettingButtonClicked', this.buttonType, this.buttonText);
                }
            }
        }
    
    </script>
    
    <style>
        .game-setting-button {
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
            margin: 2px 7px 12px 2px;
            cursor: pointer;
            font-weight: 400;
        }
    
        .button-is-active {
            background-color: salmon;
        }
    
        .disabledButton {
            background-color: #e0e1e2;
            color: #b3b3b3;
            box-shadow: none;
            /* color: */
        }
    </style>