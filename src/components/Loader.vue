<template>
    <div class="loader-wrapper" v-if="loader" style="z-index: 300 !important;">
        <div class="loader" >
            <span>{</span><span>}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Loader',
    props: {
        loader: false
    },
}
</script>

<style>

.loader-wrapper {
    width: 100%;
    height: 100%;
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    background-color: #000000;
    z-index: 160 !important;
    display: flex;
    justify-content: center;
    align-items: center;
}
.loader {
    color: #fff;
    font-family: Consolas, Menlo, Monaco, monospace;
    font-weight: bold;
    font-size: 25vh;
    opacity: 0.8;
    
}

.loader span {
    display: inline-block;
    -webkit-animation: pulse 0.35s alternate infinite ease-in-out;
    animation: pulse 0.35s alternate infinite ease-in-out;
}

.loader span:nth-child(odd) {
    -webkit-animation-delay: 0.35s;
    animation-delay: 0.35s;
}

@-webkit-keyframes pulse {
    to {
        transform: scale(0.8);
        opacity: 0.5;
    }
}

@keyframes pulse {
    to {
        transform: scale(0.8);
        opacity: 0.5;
    }
}
</style>