<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FFH4X VIP V9.4 // MOD MENU</title>
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
            background: rgba(5, 8, 20, 0.85);
            z-index: 0;
        }

        /* FLOATING ICON BUTTON */
        #floatIcon {
            position: absolute;
            top: 100px;
            left: 30px;
            width: 60px;
            height: 60px;
            background: linear-gradient(135deg, #ff3366, #ff0033);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: 700;
            font-size: 1.2rem;
            cursor: pointer;
            box-shadow: 0 0 20px rgba(255, 0, 51, 0.6);
            z-index: 9999;
            user-select: none;
            border: 2px solid #fff;
            animation: pulseIcon 2s infinite;
        }

        @keyframes pulseIcon {
            0% { transform: scale(1); box-shadow: 0 0 15px rgba(255, 0, 51, 0.6); }
            50% { transform: scale(1.08); box-shadow: 0 0 30px rgba(255, 0, 51, 0.9); }
            100% { transform: scale(1); box-shadow: 0 0 15px rgba(255, 0, 51, 0.6); }
        }

        /* MOD MENU CONTAINER */
        #modMenu {
            position: absolute;
            top: 80px;
            left: 110px;
            width: 380px;
            background: rgba(18, 22, 35, 0.95);
            border: 1px solid rgba(255, 0, 51, 0.4);
            border-radius: 14px;
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.7);
            z-index: 10000;
            display: none;
            flex-direction: column;
            overflow: hidden;
            backdrop-filter: blur(10px);
        }

        .menu-header {
            background: linear-gradient(90deg, #ff0033, #ff3366);
            color: white;
            padding: 12px 16px;
            font-weight: 600;
            font-size: 0.95rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: move;
        }

        .close-btn {
            background: none;
            border: none;
            color: white;
            font-size: 1.2rem;
            cursor: pointer;
            font-weight: 700;
        }

        .menu-body {
            padding: 15px;
            max-height: 400px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 12px;
        }

        .section-title {
            font-size: 0.75rem;
            text-transform: uppercase;
            color: #ff3366;
            font-weight: 700;
            letter-spacing: 1px;
            margin-top: 5px;
            border-bottom: 1px solid rgba(255, 51, 102, 0.2);
            padding-bottom: 3px;
        }

        .control-row {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(255, 255, 255, 0.04);
            padding: 10px 12px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.06);
        }

        .control-label {
            color: #e2e8f0;
            font-size: 0.85rem;
            font-weight: 500;
        }

        /* CUSTOM TOGGLE SWITCH */
        .switch {
            position: relative;
            display: inline-block;
            width: 44px;
            height: 22px;
        }

        .switch input { 
            opacity: 0;
            width: 0;
            height: 0;
        }

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

        input:checked + .slider {
            background-color: #ff0033;
        }

        input:checked + .slider:before {
            transform: translateX(22px);
        }

        /* LOG STATUS TOAST */
        #statusToast {
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
            z-index: 10001;
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

    <!-- FLOATING GAME ICON -->
    <div id="floatIcon" onclick="toggleMenu()">FF</div>

    <!-- VIP MOD MENU PANEL -->
    <div id="modMenu">
        <div class="menu-header" id="menuHeader">
            <span>🔥 FFH4X VIP MENU v9.4</span>
            <button class="close-btn" onclick="toggleMenu()">&times;</button>
        </div>
        <div class="menu-body">
            <div class="section-title">Combat Enhancements</div>
            <div class="control-row">
                <span class="control-label">AimLock 99% Headshot</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('AimLock Headshot Activated [99% Accuracy]')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="control-row">
                <span class="control-label">Fov Magic Bullet</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('Magic Bullet trajectory adjusted')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="control-row">
                <span class="control-label">No Recoil / Steady Aim</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('Weapon recoil parameters cleared')">
                    <span class="slider"></span>
                </label>
            </div>

            <div class="section-title">Visuals & ESP</div>
            <div class="control-row">
                <span class="control-label">ESP Line / Skeleton</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('ESP Player skeleton lines enabled')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="control-row">
                <span class="control-label">ESP Box & Distance</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('Enemy box tracking renderer active')">
                    <span class="slider"></span>
                </label>
            </div>

            <div class="section-title">System Bypass</div>
            <div class="control-row">
                <span class="control-label">Anti-Ban Protection</span>
                <label class="switch" checked>
                    <input type="checkbox" checked onchange="triggerAlert('Telemetry hooks and logs masked')">
                    <span class="slider"></span>
                </label>
            </div>
            <div class="control-row">
                <span class="control-label">Speed Hack (x2.5)</span>
                <label class="switch">
                    <input type="checkbox" onchange="triggerAlert('Movement speed multiplier locked')">
                    <span class="slider"></span>
                </label>
            </div>
        </div>
    </div>

    <!-- STATUS NOTIFICATION TOAST -->
    <div id="statusToast">Status message goes here</div>

    <script>
        function toggleMenu() {
            const menu = document.getElementById('modMenu');
            if (menu.style.display === 'flex') {
                menu.style.display = 'none';
            } else {
                menu.style.display = 'flex';
            }
        }

        function triggerAlert(message) {
            const toast = document.getElementById('statusToast');
            toast.textContent = "[✔] " + message;
            toast.style.display = 'block';
            
            setTimeout(() => {
                toast.style.display = 'none';
            }, 2500);
        }

        // Make the floating icon and menu draggable for a realistic feel
        const floatIcon = document.getElementById('floatIcon');
        let isDragging = false, startX, startY, initialX, initialY;

        floatIcon.addEventListener('mousedown', dragStart);
        document.addEventListener('mousemove', drag);
        document.addEventListener('mouseup', dragEnd);

        function dragStart(e) {
            isDragging = true;
            startX = e.clientX;
            startY = e.clientY;
            initialX = floatIcon.offsetLeft;
            initialY = floatIcon.offsetTop;
        }

        function drag(e) {
            if (!isDragging) return;
            const dx = e.clientX - startX;
            const dy = e.clientY - startY;
            floatIcon.style.left = (initialX + dx) + 'px';
            floatIcon.style.top = (initialY + dy) + 'px';
            
            // Move menu along with it
            const menu = document.getElementById('modMenu');
            menu.style.left = (initialX + dx + 80) + 'px';
            menu.style.top = (initialY + dy - 20) + 'px';
        }

        function dragEnd() {
            isDragging = false;
        }
    </script>
</body>
</html> 
