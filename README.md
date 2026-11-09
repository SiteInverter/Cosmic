# Cosmic
COSMIC SPACE — Explore the universe through an immersive, cinematic astronomy experience featuring planets, stars, and deep-space discoveries." 🌌
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>COSMIC SPACE | Explore the Universe</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
 background:#03040d;color:#fff;
 font-family:Arial,sans-serif;overflow-x:hidden
}
nav{
 position:fixed;top:0;width:100%;z-index:10;
 display:flex;justify-content:space-between;align-items:center;
 padding:20px 7%;background:#03040dcc;
 backdrop-filter:blur(12px)
}
.logo{font-size:21px;font-weight:bold;letter-spacing:3px;color:#8ddcff}
nav a{color:#ddd;text-decoration:none;margin-left:20px;font-size:13px}
.hero{
 min-height:100vh;display:flex;flex-direction:column;
 justify-content:center;align-items:center;text-align:center;
 padding:100px 20px 50px;
 background:radial-gradient(ellipse at center,#142653 0%,#080d20 40%,#03040d 75%)
}
.eyebrow{color:#8ddcff;letter-spacing:5px;font-size:12px}
h1{font-size:clamp(48px,10vw,100px);letter-spacing:8px;margin:20px 0;
 text-shadow:0 0 35px #438dff}
.hero p{color:#b5c5df;max-width:550px;line-height:1.8}
.btn{
 display:inline-block;margin-top:30px;padding:14px 27px;
 border:1px solid #73cfff;border-radius:30px;
 color:white;text-decoration:none;transition:.3s
}
.btn:hover{background:#287cb8;box-shadow:0 0 25px #287cb8}
section{padding:90px 7%;text-align:center}
h2{font-size:32px;margin-bottom:15px}
.sub{color:#93a5c3;margin-bottom:35px;line-height:1.7}
#solar{
 width:100%;height:480px;border-radius:18px;
 background:radial-gradient(circle,#101b39,#03040d);
 border:1px solid #26385c;display:block
}
.cards{
 display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
 gap:18px;margin-top:35px;text-align:left
}
.card{
 padding:24px;border:1px solid #253654;border-radius:15px;
 background:linear-gradient(145deg,#111b32,#080d1c);
 transition:.3s
}
.card:hover{transform:translateY(-5px);border-color:#70cfff}
.planet{font-size:42px;margin-bottom:15px}
.card h3{margin-bottom:10px}
.card p{color:#a8b6ce;font-size:14px;line-height:1.7}
.deep{
 background:linear-gradient(135deg,#101a38,#080916,#190e32);
 border-radius:20px;padding:55px 25px
}
.fact{color:#8ddcff;font-size:35px;font-weight:bold;margin:15px}
footer{padding:35px;text-align:center;color:#7787a3;border-top:1px solid #18243c}
@media(max-width:600px){
 nav{padding:17px 5%}
 nav a{margin-left:10px;font-size:11px}
 .logo{font-size:16px}
 section{padding:70px 5%}
 #solar{height:350px}
}
</style>
</head>
<body>

<nav>
 <div class="logo">COSMIC SPACE</div>
 <div>
  <a href="#solar-system">Solar System</a>
  <a href="#planets">Planets</a>
  <a href="#discover">Discover</a>
 </div>
</nav>

<header class="hero">
 <div class="eyebrow">A JOURNEY BEYOND THE STARS</div>
 <h1>COSMIC SPACE</h1>
 <p>Explore distant worlds, mysterious galaxies, and the endless wonders of our universe.</p>
 <a class="btn" href="#solar-system">EXPLORE THE UNIVERSE ↓</a>
</header>

<section id="solar-system">
 <h2>Our Solar System</h2>
 <p class="sub">Watch our planetary neighborhood come to life.</p>
 <canvas id="solar"></canvas>
 <p class="sub">A simplified animated model of the Sun and eight planets.</p>
</section>

<section id="planets">
 <h2>Explore the Planets</h2>
 <p class="sub">Eight worlds. Eight unique stories.</p>
 <div class="cards">
  <div class="card"><div class="planet">☿️</div><h3>Mercury</h3><p>The smallest planet and the closest world to the Sun. Its surface is covered in ancient craters.</p></div>
  <div class="card"><div class="planet">♀️</div><h3>Venus</h3><p>A scorching world with a thick atmosphere and clouds of sulfuric acid.</p></div>
  <div class="card"><div class="planet">🌍</div><h3>Earth</h3><p>Our home planet. The only world currently known to support life.</p></div>
  <div class="card"><div class="planet">🔴</div><h3>Mars</h3><p>The Red Planet, home to enormous volcanoes and ancient river valleys.</p></div>
  <div class="card"><div class="planet">🟠</div><h3>Jupiter</h3><p>The largest planet in our solar system, famous for its enormous storms.</p></div>
  <div class="card"><div class="planet">🪐</div><h3>Saturn</h3><p>A gas giant surrounded by spectacular rings made mostly of ice and rock.</p></div>
  <div class="card"><div class="planet">🔵</div><h3>Uranus</h3><p>An ice giant that rotates almost sideways compared with most planets.</p></div>
  <div class="card"><div class="planet">🔹</div><h3>Neptune</h3><p>A distant ice giant with powerful winds and a deep blue atmosphere.</p></div>
 </div>
</section>

<section id="discover">
 <div class="deep">
  <div class="eyebrow">BEYOND OUR SOLAR SYSTEM</div>
  <h2>THE UNIVERSE IS ENORMOUS</h2>
  <p class="sub">Billions of galaxies. Trillions of stars. Countless mysteries waiting to be explored.</p>
  <div class="fact">93 billion light-years</div>
  <p class="sub">Approximate diameter of the observable universe.</p>
  <a class="btn" href="#solar-system">RETURN TO THE SOLAR SYSTEM ↑</a>
 </div>
</section>

<footer>
 COSMIC SPACE © 2026 · Explore. Discover. Understand.
</footer>

<script>
const canvas=document.getElementById("solar");
let scene,camera,renderer,planets=[],sun,stars=[],animation;

function start(){
 if(!window.THREE){
  canvas.insertAdjacentHTML("afterend",
   '<p style="color:#ffaaaa;padding:15px">3D graphics could not load. Check your internet connection and refresh.</p>');
  return;
 }
 const THREE=window.THREE;
 scene=new THREE.Scene();
 camera=new THREE.PerspectiveCamera(45,canvas.clientWidth/canvas.clientHeight,.1,1000);
 camera.position.set(0,35,75);
 camera.lookAt(0,0,0);

 renderer=new THREE.WebGLRenderer({canvas,antialias:true});
 renderer.setPixelRatio(Math.min(window.devicePixelRatio,2));
 renderer.setSize(canvas.clientWidth,canvas.clientHeight,false);
 renderer.setClearColor(0x03040d);

 scene.add(new THREE.AmbientLight(0xffffff,1.3));
 const light=new THREE.PointLight(0xffffff,3,300);
 scene.add(light);

 const sunGeo=new THREE.SphereGeometry(3.5,32,32);
 const sunMat=new THREE.MeshBasicMaterial({color:0xffbb33});
 sun=new THREE.Mesh(sunGeo,sunMat);
 scene.add(sun);

 const data=[
  [0.55,7,0xb5aaa0,0.025],
  [0.85,10,0xe4b36e,0.018],
  [1,14,0x398cff,0.014],
  [0.75,18,0xd45b37,0.011],
  [2.6,25,0xd8b28a,0.006],
  [2.2,33,0xe5d1a0,0.004],
  [1.5,41,0x77ddee,0.003],
  [1.5,48,0x365bff,0.002]
 ];

 data.forEach((p,i)=>{
  const geometry=new THREE.SphereGeometry(p[0],24,24);
  const material=new THREE.MeshStandardMaterial({
   color:p[2],roughness:.8
  });
  const mesh=new THREE.Mesh(geometry,material);
  scene.add(mesh);
  planets.push({mesh,orbit:p[1],speed:p[3],angle:i*.8});

  const ringGeo=new THREE.BufferGeometry();
  const points=[];
  for(let j=0;j<=100;j++){
   const a=j/100*Math.PI*2;
   points.push(new THREE.Vector3(Math.cos(a)*p[1],0,Math.sin(a)*p[1]));
  }
  ringGeo.setFromPoints(points);
  scene.add(new THREE.Line(ringGeo,
   new THREE.LineBasicMaterial({color:0x31466b,transparent:true,opacity:.5})));
 });

 // Saturn's rings
 const saturn=planets[5].mesh;
 const ring=new THREE.Mesh(
  new THREE.RingGeometry(2.8,4.1,64),
  new THREE.MeshBasicMaterial({color:0xcbb58b,side:THREE.DoubleSide})
 );
 ring.rotation.x=Math.PI/2.5;
 saturn.add(ring);

 // Background stars
 for(let i=0;i<700;i++){
  const star=new THREE.Mesh(
   new THREE.SphereGeometry(.08,6,6),
   new THREE.MeshBasicMaterial({color:0xffffff})
  );
  star.position.set(
   (Math.random()-.5)*180,
   (Math.random()-.5)*100,
   (Math.random()-.5)*180
  );
  scene.add(star);
  stars.push(star);
 }

 function animate(){
  animation=requestAnimationFrame(animate);
  sun.rotation.y+=.002;
  planets.forEach(p=>{
   p.angle+=p.speed;
   p.mesh.position.x=Math.cos(p.angle)*p.orbit;
   p.mesh.position.z=Math.sin(p.angle)*p.orbit;
   p.mesh.rotation.y+=.01;
  });
  scene.rotation.y+=.0007;
  renderer.render(scene,camera);
 }
 animate();

 window.addEventListener("resize",resize);
}

function resize(){
 if(!renderer||!camera)return;
 const w=canvas.clientWidth,h=canvas.clientHeight;
 camera.aspect=w/h;
 camera.updateProjectionMatrix();
 renderer.setSize(w,h,false);
}

function loadThree(){
 const script=document.createElement("script");
 script.src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js";
 script.onload=start;
 script.onerror=()=>{
  const backup=document.createElement("script");
  backup.src="https://unpkg.com/three@0.128.0/build/three.min.js";
  backup.onload=start;
  backup.onerror=start;
  document.head.appendChild(backup);
 };
 document.head.appendChild(script);
}
loadThree();
</script>
</body>
</html>
