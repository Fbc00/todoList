<template>
  <div class="progresso">
        <span class="progress-value"> {{ progress }}%</span>
         <div class="progress-bar" :style="{width: progress + '%'}"></div>
  </div>
   
</template>

<script>
export default {
    props: {
        progress: {type: Number, default: 0}
    }

}
</script>

<style scoped>
    .progresso{
        position: relative;
        width: 80%;
        border: 1px solid #fff;
        border-radius: 8px;
        color: black;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .progress-bar {
        position: absolute;
        border-radius: 8px;
        height: 100%;
        background-color: aqua;
        align-self: start;

    }
    .progress-value {
        overflow: hidden;
        z-index: 99;
    }
</style>