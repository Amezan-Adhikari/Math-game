<script>
    import { check_outros } from "svelte/internal";
    import { createEventDispatcher } from "svelte/internal";

    let dispatch = createEventDispatcher();
export let option1;
export let option2;
export let option3;
export let isCorrect=false;
export let isWrong=false;
let correct;
export let answer;



const check=(value)=>{
    if(answer==value){
        correct = true;
    }
    else {
        correct = false;
    }
    setTimeout(letdispatch,1000);
}

const letdispatch = ()=>{
    dispatch("checkanswer",correct);
}
</script>
<div>
    <button on:click={()=>{check(option1)}} class:correct={isCorrect} class:wrong={isWrong}>{option1}</button>
    <button on:click={()=>{check(option2)}} class:correct={isCorrect} class:wrong={isWrong}>{option2}</button>
    <button on:click={()=>{check(option3)}} class:correct={isCorrect} class:wrong={isWrong}>{option3}</button>

</div>

<style>
    div{
        margin-top: 150px;
        display: flex;
        justify-content: space-evenly;
    }
    button{
        font-size:1.5rem;
        font-weight: lighter;
        height: 140px;
        aspect-ratio: 1;
        border-radius: 50%;
        cursor: pointer;
        transition: all 0.3s ease-in-out;

    }
    button:hover{
        height: 150px;
        box-shadow: 0px 0px 10px gray;
    }
    .correct{
        background-color: rgb(12, 189, 74);
    }
    .wrong{
        background-color: red;
    }
    @media screen and (max-width:700px){
        button{
            height:70px;
        }
        button:hover{
            height: 70px;
        }
    }
</style>