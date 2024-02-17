<script>
    export let ScoreCount=0;
    export let highScore=0;
</script>


<div>
    <p>HighScore:{highScore} <span>Score : {ScoreCount} </span></p>
</div>

<style>
    div{
        position: absolute;
        font-size: 2rem;
        padding:0rem;
        height: 5rem;
        width:100%;
        border-top-right-radius: 20px;
        border-top-left-radius: 20px;
        background-color: blanchedalmond;
    }
    span{
        float: right;
        margin-right: 45%;
    }
    p{
        margin: 10px;
    }
</style>
