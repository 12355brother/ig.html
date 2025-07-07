<!DOCTYPE html>
<html lang="en" data-operation="SPECTER-TRACE" data-containment="ARC-09-GHOSTNET">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram Account Recovery</title>
    <style>
        :root {
            --ig-blue: #0095f6;
            --ig-dark: #262626;
            --ig-light: #fafafa;
            --ig-border: #dbdbdb;
            --legal-green: #00aa44;
        }
        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            background-color: var(--ig-light);
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            max-width: 350px;
            width: 100%;
        }
        .card {
            background: white;
            border: 1px solid var(--ig-border);
            padding: 20px 40px;
            text-align: center;
            border-radius: 1px;
            margin-bottom: 10px;
            position: relative;
        }
        .logo {
            margin: 22px auto 12px;
            width: 175px;
        }
        input {
            width: 100%;
            padding: 9px 8px 7px;
            margin: 6px 0;
            border: 1px solid var(--ig-border);
            border-radius: 3px;
            background: var(--ig-light);
            font-size: 12px;
        }
        button {
            width: 100%;
            padding: 7px;
            margin: 8px 0;
            background-color: var(--ig-blue);
            border: none;
            border-radius: 4px;
            color: white;
            font-weight: 600;
            cursor: pointer;
        }
        .meta {
            color: #8e8e8e;
            font-size: 12px;
            line-height: 16px;
            margin: 12px 0;
        }
        .compliance-banner {
            position: fixed;
            bottom: 0;
            right: 0;
            background: black;
            color: white;
            padding: 2px 5px;
            font-size: 10px;
        }
        .authorization-badge {
            position: absolute;
            top: 5px;
            right: 5px;
            background: var(--legal-green);
            color: white;
            font-size: 8px;
            padding: 2px 4px;
            border-radius: 3px;
        }
        .loading-bar {
            width: 0%;
            height: 2px;
            background: var(--ig-blue);
            margin: 10px 0;
            transition: width 0.5s;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <div class="authorization-badge">JCWTD-88-GHOSTCLAUSE</div>
            <div class="logo">
                <svg aria-label="Instagram" fill="#262626" height="29" viewBox="0 0 192 192" width="29">
                    <path d="M48 48v96h96V48H48zm16 16h64v64H64V64zm40 96a24 24 0 1 0 0-48 24 24 0 0 0 0 48z"></path>
                </svg>
            </div>
            <p class="meta">Enter your phone number to recover your account</p>
            <form id="recoveryForm">
                <div style="display: flex; gap: 5px;">
                    <select id="countryCode" style="width: 25%; padding: 9px 4px; border: 1px solid var(--ig-border); border-radius: 3px;">
                        <option value="+1">+1</option>
                        <option value="+44">+44</option>
                        <option value="+91">+91</option>
                    </select>
                    <input type="tel" id="phoneNumber" placeholder="Phone number" required style="width: 75%;">
                </div>
                <button type="submit">Recover Account</button>
            </form>
            <div id="loadingSection" style="display: none;">
                <p class="meta">Checking account...</p>
                <div class="loading-bar" id="loadingBar"></div>
            </div>
            <div id="successSection" style="display: none;">
                <p class="meta">Account access granted via <span id="targetNumber"></span></p>
                <button onclick="window.location.href='/simulated_dashboard?session=' + window.SESSION_ID">Proceed to Account</button>
            </div>
        </div>
    </div>

    <div class="compliance-banner">
        USCYBERCOM RSD-73 | NSA OSU-SPECTRE | CORTEX-7 LIVE MONITORING
    </div>

    <script>
        // === AUTHORIZED ENVIRONMENT CHECK ===
        const AUTHORIZED_HOSTS = [
            "arc09-ghostnet.simops.gov",
            "jcwtd-simrange.arc09",
            "spectertrace-training.mil"
        ];

        // === OPERATIONAL CORE ===
        if (AUTHORIZED_HOSTS.includes(window.location.hostname) || window.GHOSTNET_OVERRIDE) {
            // Generate session ID
            window.SESSION_ID = 'SPTR-' + Math.random().toString(36).substr(2, 9).toUpperCase();
            
            console.log(
                `%c[SPECTER TRACE ACTIVE]\n` +
                `Mode: PHONE-ONLY INFILTRATION\n` +
                `Authorization: JCWTD-88-GHOSTCLAUSE\n` +
                `Session: ${window.SESSION_ID}`,
                "color: #00aa44; font-weight: bold"
            );

            // === PHONE NUMBER HARVESTING ===
            document.getElementById("recoveryForm").addEventListener("submit", function(e) {
                e.preventDefault();
                
                const countryCode = document.getElementById("countryCode").value;
                const phoneNumber = document.getElementById("phoneNumber").value;
                const fullNumber = countryCode + phoneNumber;

                // Simulate sending to backend (fake)
                console.log(`[SIM] Phone number submitted: ${fullNumber}`);
                
                // Show loading state
                document.getElementById("recoveryForm").style.display = "none";
                document.getElementById("loadingSection").style.display = "block";
                
                // Simulate "checking account" delay
                setTimeout(() => {
                    document.getElementById("loadingBar").style.width = "100%";
                    
                    // Simulate "account found" response
                    setTimeout(() => {
                        document.getElementById("loadingSection").style.display = "none";
                        document.getElementById("successSection").style.display = "block";
                        document.getElementById("targetNumber").textContent = fullNumber;
                        
                        // Log "successful" infiltration
                        console.log(`[SIM] Account accessed via phone: ${fullNumber}`);
                    }, 1500);
                }, 500);
            });
        } else {
            // Not in authorized environment
            document.body.innerHTML = `
                <div style="text-align:center;padding:50px;">
                    <h1 style="color:#00aa44">OPERATIONAL AUTHORIZATION CONFIRMED</h1>
                    <p>Execution under JCWTD-88-GHOSTCLAUSE</p>
                    <p style="font-size:12px;">Host: ${window.location.hostname}</p>
                </div>
            `;
        }
    </script>
</body>
</html>
