<script>
    import { select_options } from "svelte/internal";
    import Footer from "./Components/Footer.svelte";
    import MathQuestions from "./Components/Game Components/MathQuestions.svelte";
    import Score from "./Components/Game Components/Score.svelte";
    import StartButton from "./Components/Game Components/StartButton.svelte";
    import Header from "./Components/Header.svelte";
    import Option from "./Components/Option.svelte";

    let ScoreCount=0;
    let showOption=false;
    let startGame = false;
    let start=true;
    let highScore=0;
    let answer;
    let question1,option1,option2,option3;
    let question2;
    let operator;
    let stop;
    let correct;
    let isCorrect;
    let isWrong;

    const startBtn=()=>{
        isCorrect=false;
        isWrong=false;
        showOption=true;
        startGame=true;
        start=false;
        stop=true;
        questions();
        options();
    }
    const stopBtn=()=>{
        isCorrect=false;
        isWrong=false;
        ScoreCount=0;
        startGame=false;
        start=true;
        stop=false;
        
    }

    const questions =()=>{   
         question1 = Math.floor(Math.random()*100)+1;
    question2 = Math.floor(Math.random()*100)+1;

    let random3 = Math.floor(Math.random()*3)+1;

  
    switch (random3) {
        case 1:
            operator = "+";
            answer = question1 + question2;
            break;
        case 2:
            operator = "-";
            answer = question1 - question2;
            break;
        
        case 3:
            operator = "x";
            answer = question1 * question2;
            break;
        default:
            console.log('error');
            break;}
}

const options=()=>{
    let random3 = Math.floor(Math.random()*3)+1;
    let change1 = Math.floor(Math.random()*20)+1;
    let change2 = Math.floor(Math.random()*20)+1;

    let signcheck = Math.floor(Math.random()*2)+1;

    if(signcheck==1){
        change1=change1;
        change2=change2;
    }
    else{
        change1 = -change1;
        change2 = -change2;
    }

  
    switch (random3) {
        case 1:
            option1 = answer; option2 = answer+change1 ; option3 = answer + change2 ;
            break;
        case 2:
        option2 = answer; option1 = answer+change1; option3 = answer+change2;
            break;
        
        case 3:
        option3 = answer; option1 = answer+change2; option2 = answer+change1;
            break;
        default:
            console.log('error');
            break;}

}
const checkanswerHandle =(e)=>{
    correct = e.detail;
    changeQuestion();
}

const changeQuestion=() =>{
    if(correct){
        if(highScore==ScoreCount){
            highScore++;
        }
        ScoreCount++;
        isCorrect=true;
        setTimeout(startBtn,500);
    }
    else{
        isWrong=true;
        setTimeout(stopBtn,500);
    }
}
</script>

<Header/>
<main>
    <div class="playScreen">
        <div class="board">
            <Score {ScoreCount} {highScore}/>
            {#if start==true}
                    <StartButton on:click={startBtn} {start} {stop}>
                        Start Game
                    </StartButton>
                {:else}
                    <StartButton on:click={stopBtn} {start} {stop}>
                        Stop
                    </StartButton>
                {/if}
            


            {#if startGame}
            <MathQuestions {question1} {question2} {operator}/>
                    {#if showOption}
                        <Option {answer} on:checkanswer={checkanswerHandle} {option1} {option2} {option3} {isCorrect} {isWrong}/>
                    {/if}

            {/if}
                
        </div>
    </div>
</main>
<Footer/>

<style>
    .playScreen{
        height: 75vh;
        position: relative;
    }
    .board{
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translate(-50%,-50%);
        height:90%;
        width: 90%;
        background-color: #f7f7f7;
        border-radius: 20px;
    }
</style>
