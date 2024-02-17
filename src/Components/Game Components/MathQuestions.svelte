<script>
    import { select_multiple_value } from "svelte/internal";
    import { get } from "svelte/store";
    

    export let question1;
    export let operator;
    export let question2;




</script>

<div>
    <p>{question1} {operator} {question2} </p>
</div>

<style>
    div{
        height:20%;
        display: flex;
        justify-content: center;
        top:20%;
        font-size: 4rem;
    }
    p{
        padding-top: 2rem;
    }
</style>