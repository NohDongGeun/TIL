
## THREE.JS 부드러운 줌 효과

		const controls = new OrbitControls(camera, container);
		controls.enableDamping = true; // 관성 활성화
		controls.dampingFactor = 0.07; // Damping 수치
		controls.enableZoom = false; // Zoom 가능 여부

		trackControls = new TrackballControls(camera, container);
		trackControls.minDistance = minDistance; // Zoom 최소거리
		trackControls.maxDistance = maxDistance; // Zoom 최대거리
		trackControls.noRotate = true; // 회전 가능 여부
		trackControls.noPan = true; // 카메라 패닝 여부
		trackControls.noZoom = false; // Zoom 가능 여부
		trackControls.zoomSpeed = 0.5; // Zoom 스피드
		trackControls.dynamicDampingFactor = 0.1; // Damping 수치

### Controls 가 두개인 이유

OrbitControls의 damping은 좌/우는 가능하지만 줌에는 적용이 되지 않는다.
하지만 TrackballControls에서는 줌에 damping 적용 가능.
좌/우 는 OrbitControls에 의존하고 줌은 TrackballControls에 의존 해야함.
두 개의 Controls를 쓰지만 animate 하는 곳에서 아래의 코드로 sync 를 맞추어 주어야함

		function updateControls() {
			let target = controls.target;
			controls.update();
			trackControls.target.set(target.x, target.y, target.z);
			trackControls.update();
		}
			
						