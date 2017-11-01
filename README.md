# ICM_Week8: Immersive VJ Experience

var video;
var bg;

function setup(){
	createCanvas(800, 600, WEBGL);
  background(0);
  video = createCapture(VIDEO);
  video.size(200,200);
	bg = createVideo("beats.mp4");
	bg.loop();
	bg.hide();
}

function draw (){
	// video(0,0);
	background(0);

	normalMaterial();

	ambientLight(0, 0, 10, 3, 3, .8);
	pointLight(300, 300, 300, 300, 300, 1);
	// image(bg,0,0,width,height);

	translate(0,0,-600);
	push();
	translate(0,0,-2700);
	texture(bg);
	box(3300,2800);
	pop();

	var radius = width * 1.5;

	orbitControl();



// translate(0, 0, -600);
	for (let i = 0; i <=12; i++){
		for(var e = 0; e<=12; e++){
			push();
			var a = i/12 * PI;
			var b = e/12 * PI;
			translate(sin(2 * a) * radius * sin(b), cos(b) * radius / 2 , cos(2 * a) * radius * sin(b));
			if(e%2 === 0){
					push();
					// fill(80,20,64,64);
					torus(40,40);
					pop();
				}else{
					fill(150,50,50,30);
					texture(video);
					rotateZ(frameCount * 0.01);
					rotateX(frameCount * 0.01);
					rotateY(frameCount * 0.01);
					box(85,85,85);
				}
			pop();
		}
	}
}
