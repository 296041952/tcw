<!DOCTYPE>
<html>
    <head>
        <meta charset="utf-8">
        <title>Image Gallery</title>
       
        <script></script>
        <style>
            body{
                font-family: "Helvetica","Arial","serif";
                color: #333;
                background-color: #ccc;
                margin: 1em 10%;
                min-width: 1000px;
            }
            
            h1{
                color: #333;
                background-color: transparent;
            }
            
            a{
                color: #c60;
                background-color: transparent;
                font-weight: bold;
                text-decoration: none;
            }
            
            ul{
                padding: 0;
            }
            
            li{
                float:left;
                padding: 1em;
                list-style: none;
            }
            
            #imagegallery{
                list-style: none;  
            }
            
            #imagegallery li{
                display: inline;  
            }
            #imagegallery li a img{
                border: 0;
              
            }
           
        </style>
    </head>
    <body>
        <h1 >Snapshots</h1>
        <ul id="imagegallery">
            <li>
                <a href="../photograph/tooopen_sl_117572549778.jpg" title="rqwe ">
                <img src="../photograph/tooopen_sl_117572549778.jpg" alt="">
                </a>
            </li>
            <li>
                <a href="../photograph/tooopen_sl_122480112946.jpg" title="wrqa" >
                <img src="../photograph/tooopen_sl_122480112946.jpg" alt="">
                </a>
            </li>
            <li>
                <a href="../photograph/tooopen_sl_123801854694.jpg" title="wrafqs" >
                <img src="../photograph/tooopen_sl_123801854694.jpg" alt="">
                </a>
            </li>
            <li>
                <a href="../photograph/tooopen_sl_126662812857.jpg" title="wraqfs" >
                <img src="../photograph/tooopen_sl_126662812857.jpg" alt="">
                </a>
            </li>
        </ul>

        <script>
            function showpic(whichpic){
                if (!document.getElementById("placeholder")) return false;
                var source = whichpic.getAttribute("href");
                var placerholder = document.getElementById("placeholder");
                placerholder.setAttribute("src",source);
                if (document.getElementById("description")){
                    if(whichpic.getAttribute("title")){
                        var text = whichpic.getAttribute("title");
                    } else {
                        var text = "";
                    }
                        var description = document.getElementById("description");
                        description.firstChild.nodeValue = text;  
                }
                return true;
            }
            
            function prepareGallery(){
                if (!document.getElementById) return false
                if (!document.getElementsByTagName) return false;
                if (!document.getElementById("imagegallery")) return false;
                var gallery = document.getElementById("imagegallery");
                var Links = gallery.getElementsByTagName("a");
                for (var i=0; i < Links.length; i++){
                    Links[i].onclick = function(){
                        return !showpic(this);
                    }  
                }
            }
            
            function preparePlaceholder(){
                if (!document.createElement) return false;
                if (!document.createTextNode) return false;
                if (!document.getElementById) return false;
                if (!document.getElementById("imagegallery")) return false;
                var placeholder = document.createElement("img");
                placeholder.setAttribute("id","placeholder");
                placeholder.setAttribute("src","../photograph/tooopen_sl_137926458587.jpg");
                placeholder.setAttribute("alt","my image gallery");
                var description = document.createElement("p");
                description.setAttribute("id","description");
                var desctext = document.createTextNode("Choose an image");
                description.appendChild(desctext);
                var gallery = document.getElementById("imagegallery");
                insertAfter(placeholder,gallery);
                insertAfter(description,placeholder);
            }
            
            function insertAfter(newELement,targetElement){
                var parent = targetElement.parentNode;
                if (parent.lastChild == targetElement){
                    parent.appendChild(newELement);
                } else {
                    parent.insertBefore(newELement,targetElement.nextSibling);
                }
            }
            function addloadEvent(func) {
                var oldonload = window.onload;
                if (typeof window.onload != 'function'){
                    window.onload = func;
                } else {
                    window.onload = function(){
                        oldonload();
                        func();
                    }
                }
            }
            addloadEvent(prepareGallery);
            addloadEvent(preparePlaceholder);
        </script>
    </body>
</html>
