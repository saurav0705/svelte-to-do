<script>
let opacity=0.5;
$:  style = "opacity:"+opacity;

</script>

<div class="flex">
    <div class="item controls">
    <input type="range" min="0" max="1" step="0.1" bind:value={opacity}>

    </div>
    <div class="item output">
       
            <div class="child" style={style}>
            </div>
        </div>

</div>

<style type="text/scss">
    .flex{
        display: flex;
        .item{
            flex:1
        }
        .controls{

        }
        .output{
             background-color: gray;
                height:20vh;
                margin: 0;
           
                .child{
                    margin: 5vh; 
                    background-color: red;
                    height: 5vh;
                }
            
        }

    }

</style>