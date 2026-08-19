
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Garena Free Fire - Secure Account Injector v9.4</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: url('https://images.unsplash.com/photo-1542751371-adc38448a05e?q=80&w=1920&auto=format&fit=crop') no-repeat center center fixed;
            background-size: cover;
            height: 100vh;
            overflow: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(3, 7, 18, 0.9);
            z-index: 0;
        }

        /* LOGIN / ID LINK SCREEN */
        #loginScreen {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }

        .login-card {
            background: rgba(18, 22, 35, 0.95);
            border: 1px solid rgba(255, 0, 51, 0.4);
            border-radius: 16px;
            padding: 40px;
            width: 100%;
            max-width: 420px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.8);
            text-align: center;
            backdrop-filter: blur(10px);
        }

        .login-card h2 {
            color: #fff;
            font-size: 1.5rem;
            margin-bottom: 8px;
        }

        .login-card p {
            color: #94a3b8;
            font-size: 0.85rem;
            margin-bottom: 24px;
        }

        .input-group {
            margin-bottom: 20px;
            text-align: left;
        }

        .input-group label {
            display: block;
            color: #cbd5e1;
            font-size: 0.8rem;
            font-weight: 600;
            margin-bottom: 6px;
        }

        .input-group input {
            width: 100%;
            padding: 12px 16px;
            background: rgba(15, 23, 42, 0.8);
            border: 1px solid #334155;
            border-radius: 8px;
            color: #fff;
            font-size: 0.95rem;
            outline: none;
            transition: 0.3s;
        }

        .input-group input:focus {
            border-color: #ff0033;
            box-shadow: 0 0 10px rgba(255, 0, 51, 0.2);
        }

        .connect-btn {
            width: 100%;
            background: linear-gradient(135deg, #ff0033, #cc0029);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 8px;
            font-weight: 600;
            font-size: 0.95rem;
            cursor: pointer;
            transition: 0.3s;
            box-shadow: 0 4px 15px rgba(255, 0, 51, 0.4);
        }

        .connect-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(255, 0, 51, 0.6);
        }

        /* LOADING TERMINAL OVERLAY */
        #loadingScreen {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(3, 7, 18, 0.98);
            z-index: 1001;
            display: none;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #00ff66;
            font-family: 'Share Tech Mono', monospace;
            padding: 20px;
        }

        .terminal-box {
            width: 100%;
            max-width: 500px;
            background: rgba(0, 20, 5, 0.4);
            border: 1px solid #008833;
            border-radius: 8px;
            padding: 20px;
            font-size: 0.9rem;
            line-height: 1.5;
            height: 220px;
            overflow-y: hidden;
            display: flex;
            flex-direction: column;
            justify-content: flex-end;
        }

        /* DASHBOARD / MOD MENU INTERFACE */
        #dashboardScreen {
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            display: none;
            z-index: 1000;
            padding: 30px;
            overflow-y: auto;
        }

        .dash-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(18, 22, 35, 0.9);
            border: 1px solid rgba(255, 0, 51, 0.3);
            padding: 15px 25px;
            border-radius: 12px;
            margin-bottom: 25px;
            backdrop-filter: blur(10px);
        }

        .user-badge {
            color: #fff;
            font-size: 0.95rem;
            font-weight: 600;
        }

        .user-badge span {
            color: #ff0033;
        }

        .logout-btn {
            background: rgba(255, 0, 51, 0.2);
            color: #ff0033;
            border: 1px solid #ff0033;
            padding: 6px 16px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 0.8rem;
            font-weight: 600;
            transition: 0.3s;
        }

        .logout-btn:hover {
            background: #ff0033;
            color: #fff;
        }

        .controls-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 20px;
            max-width: 1100px;
            margin: 0 auto;
        }

        .control-card {
            background: rgba(18, 22, 35, 0.9);
            border: 1px solid rgba(255, 255, 255, 0.08);
            border-radius: 14px;
            padding: 20px;
            backdrop-filter: blur(10px);
        }

        .card-title {
            font-size: 0.8rem;
            text-transform: uppercase;
            color: #ff0033;
            font-weight: 700;
            letter-spacing: 1px;
            margin-bottom: 15px;
            border-bottom: 1px solid rgba(255, 0, 51, 0.2);
            padding-bottom: 6px;
        }

        .control-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.03);
            padding: 12px 14px;
            border-radius: 8px;
            margin-bottom: 10px;
            border: 1px solid rgba(255, 255, 255, 0.04);
        }

        .control-label {
            color: #e2e8f0;
            font-size: 0.88rem;
            font-weight: 500;
        }

        /* TOGGLE SWITCH */
        .switch {
            position: relative;
            display: inline-block;
            width: 44px;
            height: 22px;
        }

        .switch input { opacity: 0; width: 0; height: 0; }

        .slider {
            position: absolute;
            cursor: pointer;
            top: 0; left: 0; right: 0; bottom: 0;
            background-color: #334155;
            transition: .3s;
            border-radius: 22px;
        }

        .slider:before {
            position: absolute;
            content: "";
            height: 16px;
            width: 16px;
            left: 3px;
            bottom: 3px;
            background-color: white;
            transition: .3s;
            border-radius: 50%;
        }

        input:checked + .slider { background-color: #ff0033; }
        input:checked + .slider:before { transform: translateX(22px); }

        /* NOTIFICATION TOAST */
        #toast {
            position: fixed;
            bottom: 25px;
            right: 25px;
            background: rgba(15, 23, 42, 0.95);
            border-left: 4px solid #ff0033;
            color: #fff;
            padding: 12px 20px;
            border-radius: 8px;
            font-size: 0.85rem;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            z-index: 2000;
            display: none;
            animation: slideIn 0.3s ease forwards;
        }

        @keyframes slideIn {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
    </style>
</head>
<body>

    <!-- 1. LOGIN SCREEN -->
    <div id="loginScreen">
        <div class="login-card">
            <h2>Free Fire Portal</h2>
            <p>Enter your player UID to sync session credentials</p>
            <div class="input-group">
                <label>PLAYER UID</label>
                <input type="text" id="uidInput" placeholder="e.g. 482910492" autocomplete="off">
            </div>
            <button class="connect-btn" onclick="startConnection()">Connect & Launch</button>
        </div>
    </div>

    <!-- 2. LOADING SCREEN -->
    <div id="loadingScreen">
        <div class="terminal-box" id="terminalLog">
            <div>[+] Initializing secure tunnel socket...</div>
        </div>
    </div>

    <!-- 3. DASHBOARD / MOD MENU INTERFACE -->
    <div id="dashboardScreen">
        <div class="dash-header">
            <div class="user-badge">Connected UID: <span id="displayUid">0000000</span></div>
            <button class="logout-btn" onclick="logoutSession()">Disconnect</button>
        </div>

        <div class="controls-grid">
            <div class="control-card">
                <div class="card-title">Combat & Targeting Matrix</div>
                <div class="control-row">
                    <span class="control-label">AimLock 99% Headshot</span>
                    <label class="switch">
                        <input type="checkbox" onchange="showToast('AimLock matrix synchronized to server')">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="control-row">
                    <span class="control-label">Magic Bullet / Hitbox Offset</span>
                    <label class="switch">
                        <input type="checkbox" onchange="showToast('Hitbox redirection parameters locked')">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="control-row">
                    <span class="control-label">Zero Weapon Recoil</span>
                    <label class="switch">
                        <input type="checkbox" onchange="showToast('Recoil compensation active')">
                        <span class="slider"></span>
                    </label>
                </div>
            </div>

            <div class="control-card">
                <div class="card-title">Defense & Survival Protection</div>
                <div class="control-row">
                    <span class="control-label">Godmode / Damage Nullifier</span>
                    <label class="switch">
                        <input type="checkbox" onchange="showToast('Incoming damage packets neutralized')">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="control-row">
                    <span class="control-label">Fast Medkit / Movement</span>
                    <label class="switch">
                        <input type="checkbox" onchange="showToast('Animation delays bypassed')">
                        <span class="slider"></span>
                    </label>
                </div>
                <div class="control-row">
                    <span class="control-label">Anti-Ban Telemetry Mask</span>
                    <label class="switch" checked>
                        <input type="checkbox" checked onchange="showToast('Server security signature hidden')">
                        <span class="slider"></span>
                    </label>
                </div>
            </div>
        </div>
    </div>

    <!-- TOAST NOTIFICATION -->
    <div id="toast">Notification text</div>

    <script>
        function startConnection() {
            const uid = document.getElementById('uidInput').value.trim();
            if (!uid) {
                alert('Please enter a valid Player UID.');
                return;
            }

            document.getElementById('loginScreen').style.display = 'none';
            document.getElementById('loadingScreen').style.display = 'flex';

            const logBox = document.getElementById('terminalLog');
            const logs = [
                `[+] Binding socket to UID: ${uid}...`,
                `[+] Bypassing Garena security gatekeeper...`,
                `[+] Injecting memory payloads into server instance...`,
                `[+] Synchronization successful. Loading profile...`
            ];

            let index = 0;
            const interval = setInterval(() => {
                if (index < logs.length) {
                    logBox.innerHTML += `<div>${logs[index]}</div>`;
                    index++;
                } else {
                    clearInterval(interval);
                    setTimeout(() => {
                        document.getElementById('loadingScreen').style.display = 'none';
                        document.getElementById('dashboardScreen').style.display = 'block';
                        document.getElementById('displayUid').textContent = uid;
                        showToast('Account successfully linked & modified!');
                    }, 800);
                }
            }, 600);
        }

        function logoutSession() {
            document.getElementById('dashboardScreen').style.display = 'none';
            document.getElementById('loginScreen').style.display = 'flex';
            document.getElementById('uidInput').value = '';
        }

        function showToast(message) {
            const toast = document.getElementById('toast');
            toast.textContent = "[✔] " + message;
            toast.style.display = 'block';
            setTimeout(() => {
                toast.style.display = 'none';
            }, 2500);
        }
    </script>
</body>
</html>
