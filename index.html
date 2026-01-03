<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hệ thống cảnh báo tài xế</title>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/camera_utils/camera_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/control_utils/control_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/drawing_utils/drawing_utils.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/face_mesh/face_mesh.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@mediapipe/hands/hands.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
            max-width: 1200px;
            width: 100%;
        }

        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }

        .header h1 {
            font-size: 2em;
            margin-bottom: 10px;
        }

        .header p {
            opacity: 0.9;
            font-size: 1.1em;
        }

        .main-content {
            padding: 30px;
        }

        .video-container {
            position: relative;
            background: #000;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 20px;
        }

        video {
            width: 100%;
            display: block;
        }

        canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
        }

        .alert-drowsy {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            background: rgba(255, 0, 0, 0.9);
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 1.5em;
            font-weight: bold;
            animation: pulse 1s infinite;
            display: none;
        }

        .alert-hands {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(255, 165, 0, 0.9);
            color: white;
            padding: 20px;
            text-align: center;
            font-size: 1.5em;
            font-weight: bold;
            animation: pulse 1s infinite;
            display: none;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-top: 20px;
        }

        .stat-card {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
        }

        .stat-card h3 {
            font-size: 0.9em;
            opacity: 0.9;
            margin-bottom: 10px;
        }

        .stat-card .value {
            font-size: 2em;
            font-weight: bold;
        }

        .controls {
            display: flex;
            gap: 15px;
            justify-content: center;
            margin-top: 20px;
            flex-wrap: wrap;
        }

        button {
            padding: 15px 30px;
            font-size: 1.1em;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.3s;
            font-weight: bold;
        }

        .btn-start {
            background: #10b981;
            color: white;
        }

        .btn-start:hover {
            background: #059669;
            transform: translateY(-2px);
        }

        .btn-stop {
            background: #ef4444;
            color: white;
        }

        .btn-stop:hover {
            background: #dc2626;
            transform: translateY(-2px);
        }

        .btn-stop:disabled,
        .btn-start:disabled {
            background: #9ca3af;
            cursor: not-allowed;
            transform: none;
        }

        .info-overlay {
            position: absolute;
            top: 10px;
            left: 10px;
            background: rgba(0, 0, 0, 0.7);
            color: white;
            padding: 10px 15px;
            border-radius: 8px;
            font-size: 0.9em;
        }

        .status-indicator {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-top: 5px;
        }

        .status-dot {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            background: #10b981;
            animation: blink 2s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.3; }
        }

        .loading {
            text-align: center;
            padding: 40px;
            font-size: 1.2em;
            color: #667eea;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🚗 Hệ thống cảnh báo tài xế</h1>
            <p>Phát hiện ngủ gật và tay rời vô lăng</p>
        </div>

        <div class="main-content">
            <div class="video-container">
                <video id="video" autoplay playsinline></video>
                <canvas id="canvas"></canvas>
                
                <div id="alertDrowsy" class="alert-drowsy">
                    ⚠️ CẢNH BÁO: TÀI XẾ NGỦ GẬT!
                </div>
                
                <div id="alertHands" class="alert-hands">
                    ⚠️ CẢNH BÁO: TAY RỜI VÔ LĂNG!
                </div>

                <div class="info-overlay">
                    <div>EAR: <span id="earValue">0.00</span></div>
                    <div class="status-indicator">
                        <div class="status-dot"></div>
                        <span id="statusText">Đang theo dõi...</span>
                    </div>
                </div>
            </div>

            <div class="stats">
                <div class="stat-card">
                    <h3>Frames mắt nhắm</h3>
                    <div class="value" id="drowsyFrames">0</div>
                </div>
                <div class="stat-card">
                    <h3>Frames tay rời</h3>
                    <div class="value" id="handOffFrames">0</div>
                </div>
                <div class="stat-card">
                    <h3>Cảnh báo ngủ gật</h3>
                    <div class="value" id="drowsyAlerts">0</div>
                </div>
                <div class="stat-card">
                    <h3>Cảnh báo tay rời</h3>
                    <div class="value" id="handAlerts">0</div>
                </div>
            </div>

            <div class="controls">
                <button class="btn-start" id="startBtn">Bắt đầu giám sát</button>
                <button class="btn-stop" id="stopBtn" disabled>Dừng lại</button>
            </div>
        </div>
    </div>

    <script>
        // Cấu hình
        const CONFIG = {
            EAR_THRESHOLD: 0.25,
            CONSECUTIVE_FRAMES: 20,
            HAND_OFF_FRAMES: 30,
            ALERT_SOUND_FREQ: 1000,
            ALERT_SOUND_DURATION: 500
        };

        // Biến toàn cục
        let faceMesh, hands, camera;
        let earCounter = 0;
        let handOffCounter = 0;
        let drowsyAlertCount = 0;
        let handAlertCount = 0;
        let isDrowsyAlerting = false;
        let isHandAlerting = false;
        let audioContext;
        let isRunning = false;

        // Các chỉ số landmark cho mắt
        const LEFT_EYE = [362, 385, 387, 263, 373, 380];
        const RIGHT_EYE = [33, 160, 158, 133, 153, 144];

        // Khởi tạo Audio Context
        function initAudio() {
            audioContext = new (window.AudioContext || window.webkitAudioContext)();
        }

        // Phát âm thanh cảnh báo
        function playAlert(frequency = CONFIG.ALERT_SOUND_FREQ, duration = CONFIG.ALERT_SOUND_DURATION) {
            if (!audioContext) initAudio();
            
            const oscillator = audioContext.createOscillator();
            const gainNode = audioContext.createGain();
            
            oscillator.connect(gainNode);
            gainNode.connect(audioContext.destination);
            
            oscillator.frequency.value = frequency;
            oscillator.type = 'sine';
            
            gainNode.gain.setValueAtTime(0.3, audioContext.currentTime);
            gainNode.gain.exponentialRampToValueAtTime(0.01, audioContext.currentTime + duration / 1000);
            
            oscillator.start(audioContext.currentTime);
            oscillator.stop(audioContext.currentTime + duration / 1000);
        }

        // Tính khoảng cách Euclidean
        function distance(p1, p2) {
            return Math.sqrt(Math.pow(p2.x - p1.x, 2) + Math.pow(p2.y - p1.y, 2));
        }

        // Tính Eye Aspect Ratio (EAR)
        function calculateEAR(eyeLandmarks) {
            const A = distance(eyeLandmarks[1], eyeLandmarks[5]);
            const B = distance(eyeLandmarks[2], eyeLandmarks[4]);
            const C = distance(eyeLandmarks[0], eyeLandmarks[3]);
            
            return (A + B) / (2.0 * C);
        }

        // Lấy landmarks của mắt
        function getEyeLandmarks(landmarks, eyeIndices) {
            return eyeIndices.map(idx => landmarks[idx]);
        }

        // Xử lý kết quả Face Mesh
        function onFaceResults(results) {
            if (!isRunning) return;

            const video = document.getElementById('video');
            const canvas = document.getElementById('canvas');
            const ctx = canvas.getContext('2d');

            canvas.width = video.videoWidth;
            canvas.height = video.videoHeight;

            ctx.save();
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.drawImage(results.image, 0, 0, canvas.width, canvas.height);

            if (results.multiFaceLandmarks && results.multiFaceLandmarks.length > 0) {
                const landmarks = results.multiFaceLandmarks[0];

                // Vẽ face mesh
                window.drawConnectors(ctx, landmarks, window.FACEMESH_TESSELATION, {color: '#C0C0C070', lineWidth: 1});
                window.drawConnectors(ctx, landmarks, window.FACEMESH_RIGHT_EYE, {color: '#30FF30', lineWidth: 2});
                window.drawConnectors(ctx, landmarks, window.FACEMESH_LEFT_EYE, {color: '#30FF30', lineWidth: 2});

                // Tính EAR
                const leftEye = getEyeLandmarks(landmarks, LEFT_EYE);
                const rightEye = getEyeLandmarks(landmarks, RIGHT_EYE);
                
                const leftEAR = calculateEAR(leftEye);
                const rightEAR = calculateEAR(rightEye);
                const ear = (leftEAR + rightEAR) / 2.0;

                document.getElementById('earValue').textContent = ear.toFixed(2);

                // Kiểm tra ngủ gật
                if (ear < CONFIG.EAR_THRESHOLD) {
                    earCounter++;
                    
                    if (earCounter >= CONFIG.CONSECUTIVE_FRAMES) {
                        if (!isDrowsyAlerting) {
                            isDrowsyAlerting = true;
                            drowsyAlertCount++;
                            document.getElementById('drowsyAlerts').textContent = drowsyAlertCount;
                            document.getElementById('alertDrowsy').style.display = 'block';
                            playAlert(1000, 500);
                        }
                    }
                } else {
                    earCounter = 0;
                    isDrowsyAlerting = false;
                    document.getElementById('alertDrowsy').style.display = 'none';
                }

                document.getElementById('drowsyFrames').textContent = earCounter;
            }

            ctx.restore();
        }

        // Xử lý kết quả Hand Detection
        function onHandsResults(results) {
            if (!isRunning) return;

            const canvas = document.getElementById('canvas');
            const ctx = canvas.getContext('2d');

            let handsDetected = false;

            if (results.multiHandLandmarks && results.multiHandLandmarks.length > 0) {
                handsDetected = true;
                
                for (const landmarks of results.multiHandLandmarks) {
                    window.drawConnectors(ctx, landmarks, window.HANDS_CONNECTIONS, {color: '#00FF00', lineWidth: 3});
                    window.drawLandmarks(ctx, landmarks, {color: '#FF0000', lineWidth: 1, radius: 3});
                }
            }

            // Kiểm tra tay rời vô lăng
            if (!handsDetected) {
                handOffCounter++;
                
                if (handOffCounter >= CONFIG.HAND_OFF_FRAMES) {
                    if (!isHandAlerting) {
                        isHandAlerting = true;
                        handAlertCount++;
                        document.getElementById('handAlerts').textContent = handAlertCount;
                        document.getElementById('alertHands').style.display = 'block';
                        playAlert(1500, 300);
                    }
                }
                document.getElementById('statusText').textContent = 'Không phát hiện tay';
            } else {
                handOffCounter = 0;
                isHandAlerting = false;
                document.getElementById('alertHands').style.display = 'none';
                document.getElementById('statusText').textContent = 'Tay trên vô lăng';
            }

            document.getElementById('handOffFrames').textContent = handOffCounter;
        }

        // Khởi tạo MediaPipe Face Mesh
        function initFaceMesh() {
            faceMesh = new FaceMesh({
                locateFile: (file) => `https://cdn.jsdelivr.net/npm/@mediapipe/face_mesh/${file}`
            });

            faceMesh.setOptions({
                maxNumFaces: 1,
                refineLandmarks: true,
                minDetectionConfidence: 0.5,
                minTrackingConfidence: 0.5
            });

            faceMesh.onResults(onFaceResults);
        }

        // Khởi tạo MediaPipe Hands
        function initHands() {
            hands = new Hands({
                locateFile: (file) => `https://cdn.jsdelivr.net/npm/@mediapipe/hands/${file}`
            });

            hands.setOptions({
                maxNumHands: 2,
                modelComplexity: 1,
                minDetectionConfidence: 0.5,
                minTrackingConfidence: 0.5
            });

            hands.onResults(onHandsResults);
        }

        // Bắt đầu camera
        async function startCamera() {
            const video = document.getElementById('video');
            
            camera = new Camera(video, {
                onFrame: async () => {
                    if (isRunning) {
                        await faceMesh.send({image: video});
                        await hands.send({image: video});
                    }
                },
                width: 1280,
                height: 720
            });

            await camera.start();
        }

        // Bắt đầu giám sát
        async function startMonitoring() {
            isRunning = true;
            document.getElementById('startBtn').disabled = true;
            document.getElementById('stopBtn').disabled = false;
            
            if (!faceMesh) initFaceMesh();
            if (!hands) initHands();
            if (!camera) await startCamera();
        }

        // Dừng giám sát
        function stopMonitoring() {
            isRunning = false;
            document.getElementById('startBtn').disabled = false;
            document.getElementById('stopBtn').disabled = true;
            
            // Reset các cảnh báo
            document.getElementById('alertDrowsy').style.display = 'none';
            document.getElementById('alertHands').style.display = 'none';
        }

        // Event listeners
        document.getElementById('startBtn').addEventListener('click', startMonitoring);
        document.getElementById('stopBtn').addEventListener('click', stopMonitoring);

        // Khởi tạo khi trang load
        window.addEventListener('load', () => {
            console.log('Hệ thống cảnh báo tài xế đã sẵn sàng!');
        });
    </script>
</body>
</html>
