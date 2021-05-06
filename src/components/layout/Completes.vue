<template>
    <div id="completes-container">
        <table>
            <tr v-bind:key="completes" v-for="completes in propsdata">
                <td>{{completes[0]}}</td>
                <td>{{completes[1]}}</td>
            </tr>
        </table>
    </div>
</template>

<script>
export default {
  name: "Completes",
  props: ["propsdata"]
};
</script>

<style>
    #completes-container {
        position: fixed;
        right: 1rem;
        padding: 3rem;
        box-shadow:  0px 10px 50px #989898;
        background-color: #426b5588;
        z-index: 990;
        border-bottom-left-radius: 2rem;
        border-bottom-right-radius: 2rem;
        border-top-left-radius:1rem;
        border-top-right-radius:1rem;
        color: #fff;
    }
</style>