

<h2 style="text-align: center;"> A Test Title </h2>

<p style="text-align: center;">
<iframe src="https://drive.google.com/file/d/0B1UoLxmyYQA1ZHA3ZW5iR09sRTA/preview" width="600" height="323"></iframe>
</p>

<p style="text-align: center;"> Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.</p>

### A Point

![alt text](assets/face_space.png)

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

### Another Point

Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.

[More Information](url) 


<!DOCTYPE html>
<html>
    
    <head>
        <meta charset='utf-8'/>
        <title>TopoSketch Web App</title>
        
        <script type="text/javascript" src="./js/jsgif/LZWEncoder.js"></script>
        <script type="text/javascript" src="./js/jsgif/NeuQuant.js"></script>
        <script type="text/javascript" src="./js/jsgif/GIFEncoder.js"></script>
        <script type="text/javascript" src="./js/jsgif/b64.js"></script>

        <script type='text/javascript' src='./js/utils.js'></script>  
        <script type='text/javascript' src='./js/canvasy/canvasy.js'></script>
        <script type='text/javascript' src='./js/animation.js'></script>
        <script type='text/javascript' src='./js/grid.js'></script>
        <script type='text/javascript' src='./js/display.js'></script>
        <script type='text/javascript' src='./js/renderer.js'></script>
        <script type='text/javascript' src='./js/ui.js'></script>

        <script type='text/javascript' src='./js/main.js'></script>
        
        <link rel='stylesheet' href='./css/normalize.css'>
        <link rel='stylesheet' href='./css/skeleton.css'>
        <link rel='stylesheet' href='./css/styles.css'>

        <link href="https://fonts.googleapis.com/css?family=Open+Sans" rel="stylesheet">

    </head>

    <body onload='init();'>

        <div class='container'>
                <h1 class='title' style='margin-top:1em;'>TopoSketch Demo</h1>
                <!--<h5 class='subtitle' style='margin-top:-0.2em;line-height:1.3em;'>Generating Animations by Sketching in Conceptual Space</h5>-->
                <p>
                TopoSketch is a tool for prototyping facial animations by sketching gestures. Posing and animating a believable face is a complex process, requiring many different features to work in tandem (eg: the eyes narrowing during a smile). Using neural networks, TopoSketch creates a high level expression based control that simplies this process. Drawn gestures are then used to control the blending and timing between different expressions to create an animation. 
                </p>

                <p><a href='https://vusd.github.io/toposketch' target='_blank'>vusd.github.io/toposketch</a> </p>

                <div class='twelve columns toolbar' style="background-color:none;">
               
                <button title='Load previous grid' onclick='animation.data.prev_grid();' class='tool-button'>
                    <img src="./imgs/icons/ic_grid_left_24px.svg"> </button>
               
               <button title='Load next grid' onclick='animation.data.next_grid();' class='tool-button'>
                   <img src="./imgs/icons/ic_grid_right_24px.svg"> </button>

                <a id='save-json-button' href='default.json' target='_blank' download='path.json'>
                    <button title='Save path' class='tool-button'>
                        <p> Export Path </p>
                    </button> 
                </a>
                
                <!-- File inputs are notorious to style, so this is a workaround-->
                <div class='tool-button file-input-container'>
                    <p>Load Path</p>
                    <input id='load-json-button' class='file-input-button' type='file'>
                    </input>
                </div>

                <button id='clear-button' class='tool-button' onclick="animation.data.clear()">
                    <p>Clear Path</p>
                </button>

                <div class='tool-button' class='file-input-container'> 
                    <p>Add Grid</p>
                    <input id='load-grid-button' class='file-input-button'  type='file'></input>
                </div>

                <button id='render-button' class='tool-button'>
                    Render Animation
                </button>

            </div>
            
            <div id='anim-windows' class='twelve columns' style="background-color:red;">
                <canvas id='anim-grid' class='six columns' style="background-color:blue;"></canvas>
                <canvas id='anim-display' class='six columns'></canvas>
            </div>


            <div class='twelve columns toolbar' id='play-toolbar' style='margin-bottom:2em;'>
                <div id='play-button-container'>
                    <button id='play-button' class='tool-button'>
                        <img id='play-button-icon' src="./imgs/icons/ic_play_arrow_black_24px.svg">
                    </button>
                </div>
                <div id='timeline-container'>
                    <input type='range' id='timeline' value='5000'>
                    <p id='timeline-counter' class='readout'></p>
                </div>
            </div> 

            <h4 class='title' style='margin-top:1em;'>Rendered Animations</h4>
            <p id='no-animations-sign'>No animations yet, render something!</p>
            <div id='render-container' class='twelve columns'>
                <!--<div id='placement-guide'></div> renders will be placed before to this element-->
            </div>

            <div class='twelve columns' style="display:none;">
                <p id='fps' class='readout'></p>
            </div> 

        </div>
    </body>
</html>
