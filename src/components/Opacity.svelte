<script>
import {fade} from 'svelte/transition';
let opacity=1;
let backgroundColor = "#000000"
let textColor = "#ffffff"
let message = "click to copy to clipboard"
$:  style = "opacity:"+opacity+";background-color:"+backgroundColor+";color:"+textColor;
const toggleMessage = () => {
    message="copied"
    setTimeout(()=> message = "click to copy to clipboard",1000);
}

</script>

<div class="flex">
    <div class="item controls">
    <div class="color-control">
    <div class="label">Opacity meter</div>
    <input type="range" min="0" max="1" step="0.1" bind:value={opacity}>
    </div>
    <div class="color-control">
    <div class="label">Select background color or enter HEX Code of background color</div>
    <input type="color" bind:value={backgroundColor}/>
    <input type="text" bind:value={backgroundColor}/>
    </div>

    <div class="color-control">
    <div class="label">Select text color or enter HEX Code of text color</div>
    <input type="color" bind:value={textColor}/>
    <input type="text" bind:value={textColor}/>
    </div>

    </div>
    <div class="item output">
       
            <div class="child" style={style}>
            Excepteur qui veniam consectetur duis eiusmod. Pariatur sunt ut duis nulla labore dolor eu qui duis. Deserunt proident adipisicing laborum excepteur enim ipsum deserunt amet amet velit.
            </div>

            <div class="css-output" on:click={() => {navigator.clipboard.writeText(style);toggleMessage()}}>
            opacity : {opacity};<br>
            background-color : {backgroundColor}<br>
            color : {textColor} 
            <div class="note" transition={fade}>{message}</div>
            </div>
        </div>

</div>

<style type="text/scss">
    .flex{
        display: flex;
        width: 100%;
        .item{
            flex:1
        }
        .controls{
            .color-control{
                margin-top:4vh;
            }
            .label{
                text-transform: capitalize;
            }
            input[type="color"]{
                padding: 0;
                margin: 0;
                border: none;
                
            }
        }
        .output{
            
                // height:50vh;
                margin: 0;
           
                .child{
                    margin: 5%; 
                    padding: 2vw;
                    height: 20vh;
                    overflow: hidden;
                    cursor: no-drop;
                }
                .css-output{
                    margin: 5%;
                    padding: 2vw;
                    font-weight:700;
                    border-radius: 10px;
                    font-size: 30px; 
                    cursor: pointer;
                    background-color: rgba(222,222,222,0.3);
                    .note{
                        text-transform: capitalize;
                        color: tomato;
                        font-size: 18px;
                        font-weight: 400;
                    }
                }
        }

    }

    @media screen and (max-width:600px){
        .flex{
            display:block;
        }
    }

</style>