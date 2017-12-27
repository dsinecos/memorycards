<template>
    <div>
        <button class="button">{{ buttonText }}</button>

    </div>
</template>

<script>
    export default {
        data: function () {
            return {
                buttonText: "John Doe",
                buttonType: ""
            }
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