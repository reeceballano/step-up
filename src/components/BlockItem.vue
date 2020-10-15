<template>
    <div class="row item-row">
        <div class="item-col">
            <div class="perspective">
                <div class="cube" :style="{ 'background-color': color }"></div>
            </div>​
        </div>
    </div>
</template>

<script>
export default {
    name: "BlockItem",
    props: {
        name: {
            type: String
        },
        amounts: {
            type: String,
        },
        color: {
            type: String,
        }
    }
}
</script>

<style>

</style>