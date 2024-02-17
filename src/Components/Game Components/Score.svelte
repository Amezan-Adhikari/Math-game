<script>
    export let ScoreCount=0;
    export let highScore=0;
</script>


<div>
    
    <p>HighScore:{highScore} <br><span>Score : {ScoreCount} </span></p>
</div>

<style>
    div{
        position: absolute;
        font-size: 2rem;
        padding:0rem;
        height: 6rem;
        width:100%;
        border-top-right-radius: 20px;
        border-top-left-radius: 20px;
        background-color: blanchedalmond;
    }
    p{
        margin: 10px;
    }
    @media screen and (max-width:700px){
        
        span{
            float:none;
        }
        p{
            width:50%;
            font-size: 1.5rem;
        }
    }
</style>
