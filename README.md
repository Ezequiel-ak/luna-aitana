# luna-aitana
mi universo
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Universo de Luna Aitana</title>

<style>
body{
margin:0;
overflow:hidden;
background:black;
color:white;
font-family:Arial, sans-serif;
}

/* ESTRELLAS */
#estrellas{
position:fixed;
width:100%;
height:100%;
z-index:0;
background:black;
}

.estrella{
position:absolute;
width:2px;
height:2px;
background:white;
border-radius:50%;
}

/* INICIO */
#inicio{
position:fixed;
width:100%;
height:100%;
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
background:black;
z-index:5;
text-align:center;
}

#abrirBtn{
padding:15px 25px;
font-size:18px;
border:none;
border-radius:30px;
background:#ff4da6;
color:white;
}

/* UNIVERSO */
#universo{
position:absolute;
width:100%;
height:100%;
display:none;
z-index:2;
}

.orbita{
position:absolute;
top:50%;
left:50%;
transform-origin:center center;
animation:rotar linear infinite;
}

.foto{
position:absolute;
width:80px;
height:80px;
border-radius:50%;
object-fit:cover;
cursor:pointer;
}

#nombre{
position:absolute;
top:50%;
left:50%;
transform:translate(-50%,-50%);
font-size:20px;
color:#ffccff;
}

/* MODAL */
#modal{
position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.95);
display:none;
justify-content:center;
align-items:center;
z-index:10;
}

#modal img{
max-width:90%;
max-height:90%;
border-radius:20px;
}

@keyframes rotar{
from{transform:rotate(0deg);}
to{transform:rotate(360deg);}
}
</style>
</head>

<body>

<div id="estrellas"></div>

<div id="inicio">
<h2>¿Quieres conocer mi universo?</h2>
<button id="abrirBtn">Tocar para abrir</button>
</div>

<div id="universo">
<div id="nombre">Luna Aitana</div>
</div>

<div id="modal" onclick="cerrarModal()">
<img id="imgGrande">
</div>

<audio id="musica" src="musica.mp3"></audio>

<script>

/* ESTRELLAS */
const estrellas=document.getElementById("estrellas");
for(let i=0;i<150;i++){
let star=document.createElement("div");
star.className="estrella";
star.style.top=Math.random()*100+"%";
star.style.left=Math.random()*100+"%";
estrellas.appendChild(star);
}

/* FOTOS */
const fotos=[
"foto1.jpg","foto2.jpg","foto3.jpg",
"foto4.jpg","foto5.jpg","foto6.jpg",
"foto7.jpg","foto8.jpg","foto9.jpg"
];

const universo=document.getElementById("universo");

fotos.forEach((src,i)=>{
let orbita=document.createElement("div");
orbita.className="orbita";
orbita.style.width=(200+i*40)+"px";
orbita.style.height=(200+i*40)+"px";
orbita.style.marginLeft=-(100+i*20)+"px";
orbita.style.marginTop=-(100+i*20)+"px";
orbita.style.animationDuration=(20+i*5)+"s";

let img=document.createElement("img");
img.src=src;
img.className="foto";
img.style.top="0px";
img.style.left="50%";
img.style.transform="translateX(-50%)";

img.onclick=function(){
document.getElementById("imgGrande").src=src;
document.getElementById("modal").style.display="flex";
};

orbita.appendChild(img);
universo.appendChild(orbita);
});

/* BOTÓN ABRIR */
document.getElementById("abrirBtn").addEventListener("click",function(){

document.getElementById("inicio").style.display="none";
universo.style.display="block";

/* música */
let musica=document.getElementById("musica");
musica.play().catch(function(){});

});

/* CERRAR MODAL */
function cerrarModal(){
document.getElementById("modal").style.display="none";
}

</script>

</body>
</html>
