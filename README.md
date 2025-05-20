
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>3D������վ</title>
    <style>
        body { margin: 0; }
        canvas { display: block; }
        h1 { position: absolute; top: 10px; left: 10px; color: white; font-family: Arial; }
    </style>
</head>
<body>
    <h1>�Ұ��㣡</h1>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <script>
        // Three.js���룺����3D����
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        // ����3D���ļ�����
        const heartShape = new THREE.Shape();
        heartShape.moveTo(25, 25);
        heartShape.bezierCurveTo(25, 25, 20, 0, 0, 0);
        heartShape.bezierCurveTo(-30, 0, -30, 35, -30, 35);
        heartShape.bezierCurveTo(-30, 55, -10, 77, 25, 95);
        heartShape.bezierCurveTo(60, 77, 80, 55, 80, 35);
        heartShape.bezierCurveTo(80, 35, 80, 0, 50, 0);
        heartShape.bezierCurveTo(35, 0, 25, 25, 25, 25);

        const extrudeSettings = { depth: 8, bevelEnabled: true, bevelSegments: 2, steps: 2, bevelSize: 1, bevelThickness: 1 };
        const geometry = new THREE.ExtrudeGeometry(heartShape, extrudeSettings);
        const material = new THREE.MeshPhongMaterial({ color: 0xff0000 });
        const heart = new THREE.Mesh(geometry, material);
        scene.add(heart);

        camera.position.z = 50;

        const light = new THREE.PointLight(0xffffff, 1, 100);
        light.position.set(10, 10, 10);
        scene.add(light);

        function animate() {
            requestAnimationFrame(animate);
            heart.rotation.x += 0.01;
            heart.rotation.y += 0.01;
            renderer.render(scene, camera);
        }
        animate();
    </script>
</body>
</html>
