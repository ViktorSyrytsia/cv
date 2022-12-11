<script>
	let cnv;
	setTimeout(() => {
		if (cnv) {
			const cnv = document.querySelector(`canvas`);
			const ctx = cnv.getContext(`2d`);

			let centerX = 0;
			let centerY = 0;
			function init() {
				cnv.width = innerWidth;
				cnv.height = innerHeight;

				centerX = cnv.width / 2;
				centerY = cnv.height / 2;
			}
			init();

			const numberOfRings = 5;
			const ringRadiusOffset = 50;
			const ringRadius = 300;
			const waveOffset = 19;
			const velocity = 0.5;
			const colors = [`#064e3b`, `#047857`, `#10b981`, `#6ee7b7`, `#d1fae5`];
			// colors.reverse();
			let startAngle = 0;

			function updateRings() {
				for (let i = 1; i <= numberOfRings; i++) {
					let radius = i * ringRadiusOffset + ringRadius;
					let offsetAngle = (i * waveOffset * Math.PI) / 180;
					let color = colors[i];
					drawRing(radius, color, offsetAngle);
				}

				startAngle >= 360 ? (startAngle = 0) : (startAngle += velocity);
			}

			const maxWavesAmplitude = 23;
			const numberOfWaves = 3;

			function drawRing(radius, color, offsetAngle) {
				ctx.strokeStyle = color;
				ctx.lineWidth = 2;

				ctx.beginPath();

				for (let j = -180; j < 180; j++) {
					let currentAngle = ((j + startAngle) * Math.PI) / 180;
					let displacement = 0;
					let now = Math.abs(j);

					if (now > 30) {
						displacement = (now - 30) / 120;
					}

					if (displacement >= 1) {
						displacement = 1;
					}

					let waveAmplitude =
						radius +
						displacement *
							Math.sin((currentAngle + offsetAngle) * numberOfWaves) *
							maxWavesAmplitude;
					let x = centerX + Math.cos(currentAngle) * waveAmplitude;
					let y = centerY + Math.sin(currentAngle) * waveAmplitude;
					j > -180 ? ctx.lineTo(x, y) : ctx.moveTo(x, y);
				}
				ctx.closePath();
				ctx.stroke();
			}

			function loop() {
				cnv.width |= 0; // ctx.clearRect(0, 0, cnv.width, cnv.height);
				updateRings();
				requestAnimationFrame(loop);
			}
			loop();

			window.addEventListener(`resize`, init);
		}
	}, 0);
</script>

<div
	class="absolute top-0 bottom-0 left-0 right-0 z-10 flex justify-center items-center min-h-screen opacity-80"
>
	<canvas bind:this={cnv} />
</div>
