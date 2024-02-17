<script>
export let stop = false;
export let start = true;
</script>

<button on:click class:stop={stop} class:start={start}>
    <slot></slot>
</button>

<style>
    .start{
        position:absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%,-50%);
        height: min-content;
        font-size: 4rem;
        font-weight: lighter;
        text-align: center;
        border-radius: 1rem;
        box-shadow: 0px 0px 5px gray;
        background-color: rgb(22, 228, 125);
    }
    .stop{
        position:absolute;
        top: 5%;
        right:5%;
        height: min-content;
        width: 100px;
        font-size: 1rem;
        font-weight: normal;
        text-align: center;
        color: red;
        border-radius: 1rem;
        box-shadow: 0px 0px 5px rgb(189, 32, 32);
        background-color: transparent;

    }
</style>