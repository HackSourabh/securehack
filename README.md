# securehack
In today's hyper-digitized world, safeguarding information, systems, and networks from malicious attacks is paramount. Our Cyber Security &amp; Ethical Hacking Platform is designed to provide comprehensive protection and proactive defense against cyber threats.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SecureHack - Authentication</title>
    <style>
        :root {
            --primary-color: #0c0f16;
            --secondary-color: #1a1f2e;
            --accent-color: #00ff8c;
            --text-color: #e0e0e0;
            --error-color: #ff3e3e;
            --success-color: #00c853;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Courier New', monospace;
        }
        
        body {
            background-color: var(--primary-color);
            color: var(--text-color);
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
            background-image: 
                radial-gradient(rgba(0, 255, 140, 0.03) 2px, transparent 2px),
                radial-gradient(rgba(0, 255, 140, 0.02) 2px, transparent 2px);
            background-size: 40px 40px;
            background-position: 0 0, 20px 20px;
        }
        
        .container {
            display: flex;
            width: 100%;
            max-width: 1000px;
            height: 600px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
            border-radius: 8px;
            overflow: hidden;
        }
        
        .info-section {
            background-color: var(--secondary-color);
            flex: 1;
            padding: 40px;
            position: relative;
            overflow: hidden;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }
        
        .info-section::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.4)),
                url('/api/placeholder/500/600') center/cover no-repeat;
            opacity: 0.6;
            z-index: 0;
        }
        
        .info-content {
            position: relative;
            z-index: 1;
        }
        
        .logo {
            font-size: 28px;
            font-weight: bold;
            margin-bottom: 20px;
            color: var(--accent-color);
        }
        
        .logo span {
            color: var(--text-color);
        }
        
        .tagline {
            font-size: 24px;
            margin-bottom: 20px;
        }
        
        .features {
            margin-top: 30px;
        }
        
        .feature {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .feature-icon {
            margin-right: 10px;
            color: var(--accent-color);
            font-weight: bold;
        }
        
        .footer {
            margin-top: auto;
            font-size: 14px;
            opacity: 0.7;
            position: relative;
            z-index: 1;
        }
        
        .auth-section {
            background-color: var(--primary-color);
            flex: 1;
            padding: 40px;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }
        
        .auth-tabs {
            display: flex;
            margin-bottom: 30px;
        }
        
        .tab {
            padding: 10px 20px;
            cursor: pointer;
            border-bottom: 2px solid transparent;
            font-size: 16px;
            transition: all 0.3s ease;
        }
        
        .tab.active {
            border-bottom: 2px solid var(--accent-color);
            color: var(--accent-color);
        }
        
        .tab:hover:not(.active) {
            color: rgba(0, 255, 140, 0.7);
        }
        
        .auth-form {
            display: none;
        }
        
        .auth-form.active {
            display: block;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-size: 14px;
        }
        
        .input-group {
            position: relative;
        }
        
        .form-control {
            width: 100%;
            padding: 12px 15px;
            background-color: var(--secondary-color);
            border: 1px solid #2c3347;
            border-radius: 4px;
            color: var(--text-color);
            font-size: 14px;
            transition: all 0.3s ease;
        }
        
        .form-control:focus {
            outline: none;
            border-color: var(--accent-color);
            box-shadow: 0 0 0 2px rgba(0, 255, 140, 0.2);
        }
        
        .password-toggle {
            position: absolute;
            right: 10px;
            top: 50%;
            transform: translateY(-50%);
            cursor: pointer;
            color: #878787;
            font-size: 14px;
            user-select: none;
        }
        
        .password-requirements {
            margin-top: 8px;
            font-size: 12px;
            color: #878787;
        }
        
        .password-requirement {
            display: flex;
            align-items: center;
            margin-bottom: 4px;
        }
        
        .requirement-icon {
            margin-right: 5px;
            font-size: 10px;
        }
        
        .invalid {
            color: var(--error-color);
        }
        
        .valid {
            color: var(--success-color);
        }
        
        .captcha-container {
            margin-bottom: 20px;
            padding: 10px;
            background-color: var(--secondary-color);
            border-radius: 4px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .captcha-img {
            background-color: #2c3347;
            height: 60px;
            width: 100%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 20px;
            letter-spacing: 5px;
            font-style: italic;
            position: relative;
            overflow: hidden;
            margin-bottom: 10px;
            user-select: none;
        }
        
        .captcha-img::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(
                45deg,
                transparent,
                transparent 10px,
                rgba(0, 0, 0, 0.05) 10px,
                rgba(0, 0, 0, 0.05) 20px
            );
        }
        
        .captcha-img::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(
                to bottom,
                rgba(255, 255, 255, 0.1),
                transparent 50%,
                rgba(0, 0, 0, 0.1)
            );
        }
        
        .captcha-refresh {
            align-self: flex-end;
            color: var(--accent-color);
            cursor: pointer;
            font-size: 12px;
        }
        
        .checkbox-group {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .checkbox-group input {
            margin-right: 10px;
        }
        
        .checkbox-group label {
            font-size: 14px;
            margin: 0;
        }
        
        .btn {
            width: 100%;
            padding: 12px;
            border: none;
            border-radius: 4px;
            background-color: var(--accent-color);
            color: #000;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 20px;
        }
        
        .btn:hover {
            background-color: rgba(0, 255, 140, 0.8);
        }
        
        .btn:active {
            transform: translateY(1px);
        }
        
        .auth-separator {
            display: flex;
            align-items: center;
            margin: 20px 0;
            color: #878787;
            font-size: 14px;
        }
        
        .auth-separator::before,
        .auth-separator::after {
            content: "";
            flex: 1;
            height: 1px;
            background-color: #2c3347;
        }
        
        .auth-separator::before {
            margin-right: 10px;
        }
        
        .auth-separator::after {
            margin-left: 10px;
        }
        
        .social-auth {
            display: flex;
            justify-content: space-between;
        }
        
        .social-btn {
            flex: 1;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 10px;
            background-color: var(--secondary-color);
            border-radius: 4px;
            margin: 0 5px;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .social-btn:hover {
            background-color: rgba(28, 33, 46, 1);
        }
        
        .error-message {
            color: var(--error-color);
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .success-message {
            color: var(--success-color);
            font-size: 14px;
            margin-top: 5px;
            display: none;
        }
        
        .forgot-password {
            text-align: right;
            margin-top: -15px;
            margin-bottom: 20px;
        }
        
        .forgot-password a {
            color: #878787;
            font-size: 12px;
            text-decoration: none;
        }
        
        .forgot-password a:hover {
            color: var(--accent-color);
        }
        
        .terminal-line {
            overflow: hidden;
            white-space: nowrap;
            border-right: 0.15em solid var(--accent-color);
            width: 0;
            animation: typing 3.5s steps(30, end) forwards, blink-caret 0.75s step-end infinite;
            animation-delay: 0.5s;
        }
        
        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }
        
        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--accent-color) }
        }
        
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
                height: auto;
            }
            
            .info-section {
                padding: 30px;
                min-height: 300px;
            }
            
            .auth-section {
                padding: 30px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="info-section">
            <div class="info-content">
                <div class="logo">Secure<span>Hack</span></div>
                <h1 class="tagline">Ethical Hacking & Cybersecurity Training Platform</h1>
                <p class="terminal-line">Learn. Practice. Secure.</p>
                <div class="features">
                    <div class="feature">
                        <span class="feature-icon">→</span>
                        <span>Interactive CTF Challenges</span>
                    </div>
                    <div class="feature">
                        <span class="feature-icon">→</span>
                        <span>Virtualized Lab Environments</span>
                    </div>
                    <div class="feature">
                        <span class="feature-icon">→</span>
                        <span>Expert-Led Security Courses</span>
                    </div>
                    <div class="feature">
                        <span class="feature-icon">→</span>
                        <span>Security Community Access</span>
                    </div>
                </div>
            </div>
            <div class="footer">
                © 2025 SecureHack. All rights reserved.
            </div>
        </div>
        
        <div class="auth-section">
            <div class="auth-tabs">
                <div class="tab active" id="login-tab">Sign In</div>
                <div class="tab" id="register-tab">Register</div>
            </div>
            
            <form class="auth-form active" id="login-form">
                <div class="form-group">
                    <label for="login-username">Username or Email</label>
                    <div class="input-group">
                        <input type="text" class="form-control" id="login-username">
                    </div>
                    <div class="error-message" id="login-username-error">Please enter a valid username or email</div>
                </div>
                
                <div class="form-group">
                    <label for="login-password">Password</label>
                    <div class="input-group">
                        <input type="password" class="form-control" id="login-password">
                        <span class="password-toggle" id="login-password-toggle">show</span>
                    </div>
                    <div class="error-message" id="login-password-error">Please enter your password</div>
                </div>
                
                <div class="forgot-password">
                    <a href="#">Forgot password?</a>
                </div>
                
                <div class="checkbox-group">
                    <input type="checkbox" id="remember-me">
                    <label for="remember-me">Remember me on this device</label>
                </div>
                
                <button type="submit" class="btn" id="login-btn">Sign In</button>
                
                <div class="success-message" id="login-success">Successfully logged in! Redirecting...</div>
                <div class="error-message" id="login-error">Invalid username or password. Please try again.</div>
                
                <div class="auth-separator">Or sign in with</div>
                
                <div class="social-auth">
                    <div class="social-btn">G</div>
                    <div class="social-btn">f</div>
                    <div class="social-btn">in</div>
                    <div class="social-btn">GH</div>
                </div>
            </form>
            
            <form class="auth-form" id="register-form">
                <div class="form-group">
                    <label for="register-username">Username</label>
                    <div class="input-group">
                        <input type="text" class="form-control" id="register-username">
                    </div>
                    <div class="error-message" id="register-username-error">Username must be 3-20 characters and only contain letters, numbers, and underscores</div>
                </div>
                
                <div class="form-group">
                    <label for="register-email">Email</label>
                    <div class="input-group">
                        <input type="email" class="form-control" id="register-email">
                    </div>
                    <div class="error-message" id="register-email-error">Please enter a valid email address</div>
                </div>
                
                <div class="form-group">
                    <label for="register-password">Password</label>
                    <div class="input-group">
                        <input type="password" class="form-control" id="register-password">
                        <span class="password-toggle" id="register-password-toggle">show</span>
                    </div>
                    <div class="password-requirements">
                        <div class="password-requirement" id="req-length">
                            <span class="requirement-icon invalid">✕</span>
                            <span>At least 12 characters</span>
                        </div>
                        <div class="password-requirement" id="req-uppercase">
                            <span class="requirement-icon invalid">✕</span>
                            <span>At least 1 uppercase letter</span>
                        </div>
                        <div class="password-requirement" id="req-lowercase">
                            <span class="requirement-icon invalid">✕</span>
                            <span>At least 1 lowercase letter</span>
                        </div>
                        <div class="password-requirement" id="req-number">
                            <span class="requirement-icon invalid">✕</span>
                            <span>At least 1 number</span>
                        </div>
                        <div class="password-requirement" id="req-special">
                            <span class="requirement-icon invalid">✕</span>
                            <span>At least 1 special character</span>
                        </div>
                    </div>
                </div>
                
                <div class="form-group">
                    <label for="register-confirm-password">Confirm Password</label>
                    <div class="input-group">
                        <input type="password" class="form-control" id="register-confirm-password">
                    </div>
                    <div class="error-message" id="register-confirm-password-error">Passwords do not match</div>
                </div>
                
                <div class="captcha-container">
                    <div class="captcha-img" id="captcha-img">5X7A2P</div>
                    <span class="captcha-refresh" id="captcha-refresh">↻ Refresh</span>
                </div>
                
                <div class="form-group">
                    <label for="captcha-input">Enter CAPTCHA</label>
                    <div class="input-group">
                        <input type="text" class="form-control" id="captcha-input">
                    </div>
                    <div class="error-message" id="captcha-error">Invalid CAPTCHA. Please try again.</div>
                </div>
                
                <div class="checkbox-group">
                    <input type="checkbox" id="terms">
                    <label for="terms">I agree to the <a href="#" style="color: var(--accent-color);">Terms of Service</a> and <a href="#" style="color: var(--accent-color);">Privacy Policy</a></label>
                </div>
                
                <button type="submit" class="btn" id="register-btn">Create Account</button>
                
                <div class="success-message" id="register-success">Account created successfully! Please check your email to verify your account.</div>
                <div class="error-message" id="register-error">There was an error creating your account. Please try again.</div>
            </form>
        </div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Tab switching
            const loginTab = document.getElementById('login-tab');
            const registerTab = document.getElementById('register-tab');
            const loginForm = document.getElementById('login-form');
            const registerForm = document.getElementById('register-form');
            
            loginTab.addEventListener('click', function() {
                loginTab.classList.add('active');
                registerTab.classList.remove('active');
                loginForm.classList.add('active');
                registerForm.classList.remove('active');
            });
            
            registerTab.addEventListener('click', function() {
                registerTab.classList.add('active');
                loginTab.classList.remove('active');
                registerForm.classList.add('active');
                loginForm.classList.remove('active');
            });
            
            // Password toggles
            const loginPasswordToggle = document.getElementById('login-password-toggle');
            const loginPassword = document.getElementById('login-password');
            
            loginPasswordToggle.addEventListener('click', function() {
                if (loginPassword.type === 'password') {
                    loginPassword.type = 'text';
                    loginPasswordToggle.textContent = 'hide';
                } else {
                    loginPassword.type = 'password';
                    loginPasswordToggle.textContent = 'show';
                }
            });
            
            const registerPasswordToggle = document.getElementById('register-password-toggle');
            const registerPassword = document.getElementById('register-password');
            
            registerPasswordToggle.addEventListener('click', function() {
                if (registerPassword.type === 'password') {
                    registerPassword.type = 'text';
                    registerPasswordToggle.textContent = 'hide';
                } else {
                    registerPassword.type = 'password';
                    registerPasswordToggle.textContent = 'show';
                }
            });
            
            // Password validation
            const passwordRequirements = {
                length: false,
                uppercase: false,
                lowercase: false,
                number: false,
                special: false
            };
            
            const reqLength = document.getElementById('req-length');
            const reqUppercase = document.getElementById('req-uppercase');
            const reqLowercase = document.getElementById('req-lowercase');
            const reqNumber = document.getElementById('req-number');
            const reqSpecial = document.getElementById('req-special');
            
            registerPassword.addEventListener('input', function() {
                const password = registerPassword.value;
                
                // Check length
                passwordRequirements.length = password.length >= 12;
                updateRequirement(reqLength, passwordRequirements.length);
                
                // Check uppercase
                passwordRequirements.uppercase = /[A-Z]/.test(password);
                updateRequirement(reqUppercase, passwordRequirements.uppercase);
                
                // Check lowercase
                passwordRequirements.lowercase = /[a-z]/.test(password);
                updateRequirement(reqLowercase, passwordRequirements.lowercase);
                
                // Check number
                passwordRequirements.number = /[0-9]/.test(password);
                updateRequirement(reqNumber, passwordRequirements.number);
                
                // Check special
                passwordRequirements.special = /[^A-Za-z0-9]/.test(password);
                updateRequirement(reqSpecial, passwordRequirements.special);
            });
            
            function updateRequirement(element, valid) {
                const icon = element.querySelector('.requirement-icon');
                if (valid) {
                    icon.textContent = '✓';
                    icon.classList.remove('invalid');
                    icon.classList.add('valid');
                } else {
                    icon.textContent = '✕';
                    icon.classList.remove('valid');
                    icon.classList.add('invalid');
                }
            }
            
            // CAPTCHA refresh
            const captchaRefresh = document.getElementById('captcha-refresh');
            const captchaImg = document.getElementById('captcha-img');
            
            captchaRefresh.addEventListener('click', function() {
                // Generate a random CAPTCHA code
                const characters = 'ABCDEFGHJKLMNPQRSTUVWXYZ23456789';
                let captcha = '';
                for (let i = 0; i < 6; i++) {
                    captcha += characters.charAt(Math.floor(Math.random() * characters.length));
                }
                captchaImg.textContent = captcha;
            });
            
            // Form submission
            const loginBtn = document.getElementById('login-btn');
            const loginSuccess = document.getElementById('login-success');
            const loginError = document.getElementById('login-error');
            
            loginForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('login-username').value;
                const password = document.getElementById('login-password').value;
                
                // Simple validation
                let valid = true;
                
                if (!username) {
                    document.getElementById('login-username-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('login-username-error').style.display = 'none';
                }
                
                if (!password) {
                    document.getElementById('login-password-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('login-password-error').style.display = 'none';
                }
                
                if (valid) {
                    // Simulate authentication
                    if (username === 'admin@securehack.com' && password === 'SecureP@ssword123') {
                        loginSuccess.style.display = 'block';
                        loginError.style.display = 'none';
                        setTimeout(() => {
                            window.location.href = '/dashboard';
                        }, 1500);
                    } else {
                        loginError.style.display = 'block';
                        loginSuccess.style.display = 'none';
                    }
                }
            });
            
            const registerBtn = document.getElementById('register-btn');
            const registerSuccess = document.getElementById('register-success');
            const registerError = document.getElementById('register-error');
            
            registerForm.addEventListener('submit', function(e) {
                e.preventDefault();
                
                const username = document.getElementById('register-username').value;
                const email = document.getElementById('register-email').value;
                const password = document.getElementById('register-password').value;
                const confirmPassword = document.getElementById('register-confirm-password').value;
                const captchaInput = document.getElementById('captcha-input').value;
                const termsChecked = document.getElementById('terms').checked;
                
                // Simple validation
                let valid = true;
                
                // Username validation
                if (!username || !/^[a-zA-Z0-9_]{3,20}$/.test(username)) {
                    document.getElementById('register-username-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('register-username-error').style.display = 'none';
                }
                
                // Email validation
                if (!email || !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email)) {
                    document.getElementById('register-email-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('register-email-error').style.display = 'none';
                }
                
                // Password confirmation
                if (password !== confirmPassword) {
                    document.getElementById('register-confirm-password-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('register-confirm-password-error').style.display = 'none';
                }
                
                // Password requirements check
                if (!Object.values(passwordRequirements).every(req => req)) {
                    valid = false;
                }
                
                // CAPTCHA validation
                if (captchaInput.toUpperCase() !== captchaImg.textContent) {
                    document.getElementById('captcha-error').style.display = 'block';
                    valid = false;
                } else {
                    document.getElementById('captcha-error').style.display = 'none';
                }
                
                // Terms check
                if (!termsChecked) {
                    valid = false;
                }
                
                if (valid) {
                    // Simulate registration
                    registerSuccess.style.display = 'block';
                    registerError.style.display = 'none';
                } else {
                    registerError.style.display = 'block';
                    registerSuccess.style.display = 'none';
                }
            });
        });
    </script>
</body>
</html>





<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SecureHack - Dashboard</title>
    <style>
        :root {
            --primary-color: #0c0f16;
            --secondary-color: #1a1f2e;
            --accent-color: #00ff8c;
            --text-color: #e0e0e0;
            --error-color: #ff3e3e;
            --success-color: #00c853;
            --card-bg: #1a1f2e;
            --nav-hover: #282f3e;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Courier New', monospace;
        }
        
        body {
            background-color: var(--primary-color);
            color: var(--text-color);
            min-height: 100vh;
            background-image: 
                radial-gradient(rgba(0, 255, 140, 0.03) 2px, transparent 2px),
                radial-gradient(rgba(0, 255, 140, 0.02) 2px, transparent 2px);
            background-size: 40px 40px;
            background-position: 0 0, 20px 20px;
        }
        
        /* Header & Navigation */
        header {
            background-color: var(--secondary-color);
            box-shadow: 0 1px 10px rgba(0, 0, 0, 0.3);
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-container {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px 30px;
            max-width: 1400px;
            margin: 0 auto;
        }
        
        .logo {
            font-size: 24px;
            font-weight: bold;
            color: var(--accent-color);
            text-decoration: none;
            display: flex;
            align-items: center;
        }
        
        .logo span {
            color: var(--text-color);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 25px;
            position: relative;
        }
        
        nav ul li a {
            color: var(--text-color);
            text-decoration: none;
            font-size: 16px;
            padding: 10px 15px;
            border-radius: 4px;
            transition: all 0.3s ease;
        }
        
        nav ul li a:hover {
            background-color: var(--nav-hover);
        }
        
        .active {
            border-bottom: 2px solid var(--accent-color);
            color: var(--accent-color);
        }
        
        .user-menu {
            position: relative;
        }
        
        .user-avatar {
            width: 36px;
            height: 36px;
            border-radius: 50%;
            background-color: var(--accent-color);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary-color);
            font-weight: bold;
            cursor: pointer;
        }
        
        .dropdown-menu {
            position: absolute;
            top: 45px;
            right: 0;
            background-color: var(--secondary-color);
            border-radius: 4px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            width: 200px;
            display: none;
            z-index: 10;
        }
        
        .dropdown-menu.show {
            display: block;
        }
        
        .dropdown-menu ul {
            list-style: none;
            padding: 5px 0;
        }
        
        .dropdown-menu ul li {
            margin: 0;
        }
        
        .dropdown-menu ul li a {
            display: block;
            padding: 10px 20px;
            color: var(--text-color);
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .dropdown-menu ul li a:hover {
            background-color: var(--nav-hover);
        }
        
        .dropdown-divider {
            height: 1px;
            background-color: #2c3347;
            margin: 5px 0;
        }
        
        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 30px auto;
            padding: 0 20px;
        }
        
        .welcome-banner {
            background-color: var(--secondary-color);
            border-radius: 10px;
            padding: 30px;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .welcome-text {
            flex: 2;
        }
        
        .welcome-text h1 {
            font-size: 28px;
            margin-bottom: 10px;
            color: var(--accent-color);
        }
        
        .welcome-text p {
            font-size: 16px;
            margin-bottom: 15px;
        }
        
        .welcome-actions {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
        }
        
        .btn {
            padding: 12px 25px;
            border: none;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            text-align: center;
        }
        
        .btn-primary {
            background-color: var(--accent-color);
            color: #000;
        }
        
        .btn-primary:hover {
            background-color: rgba(0, 255, 140, 0.8);
        }
        
        .btn-secondary {
            background-color: transparent;
            border: 1px solid var(--accent-color);
            color: var(--accent-color);
            margin-top: 10px;
        }
        
        .btn-secondary:hover {
            background-color: rgba(0, 255, 140, 0.1);
        }
        
        .section-header {
            margin-bottom: 20px;
            border-bottom: 1px solid #2c3347;
            padding-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .section-header h2 {
            font-size: 24px;
            color: var(--accent-color);
        }
        
        .video-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
            gap: 25px;
            margin-bottom: 40px;
        }
        
        .video-card {
            background-color: var(--card-bg);
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transition: transform 0.3s ease;
        }
        
        .video-card:hover {
            transform: translateY(-5px);
        }
        
        .video-thumbnail {
            position: relative;
            height: 180px;
            overflow: hidden;
            background-color: #2c3347;
        }
        
        .video-thumbnail img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        
        .video-duration {
            position: absolute;
            bottom: 10px;
            right: 10px;
            background-color: rgba(0, 0, 0, 0.7);
            color: var(--text-color);
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .mentor-badge {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: var(--accent-color);
            color: #000;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: bold;
        }
        
        .video-info {
            padding: 15px;
        }
        
        .video-title {
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 8px;
            line-height: 1.4;
        }
        
        .video-meta {
            display: flex;
            justify-content: space-between;
            font-size: 14px;
            color: #878787;
            margin-bottom: 10px;
        }
        
        .video-description {
            font-size: 14px;
            line-height: 1.5;
            margin-bottom: 15px;
            color: #a1a1a1;
            display: -webkit-box;
            -webkit-line-clamp: 3;
            -webkit-box-orient: vertical;
            overflow: hidden;
        }
        
        .video-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 5px;
        }
        
        .tag {
            background-color: #2c3347;
            color: #878787;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 12px;
        }
        
        .view-all {
            color: var(--accent-color);
            text-decoration: none;
            font-size: 16px;
            display: flex;
            align-items: center;
        }
        
        .view-all:hover {
            text-decoration: underline;
        }
        
        .view-all span {
            margin-left: 5px;
        }
        
        /* Footer */
        footer {
            background-color: var(--secondary-color);
            padding: 30px 0;
            margin-top: 50px;
        }
        
        .footer-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 30px;
        }
        
        .footer-section h3 {
            color: var(--accent-color);
            font-size: 18px;
            margin-bottom: 15px;
        }
        
        .footer-section ul {
            list-style: none;
        }
        
        .footer-section ul li {
            margin-bottom: 10px;
        }
        
        .footer-section ul li a {
            color: #878787;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        
        .footer-section ul li a:hover {
            color: var(--text-color);
        }
        
        .footer-bottom {
            text-align: center;
            margin-top: 30px;
            padding-top: 20px;
            border-top: 1px solid #2c3347;
            color: #878787;
            font-size: 14px;
        }
        
        /* Mobile Responsiveness */
        @media (max-width: 768px) {
            .header-container {
                flex-direction: column;
                padding: 15px;
            }
            
            nav ul {
                margin-top: 15px;
                justify-content: center;
                flex-wrap: wrap;
            }
            
            nav ul li {
                margin: 5px;
            }
            
            .welcome-banner {
                flex-direction: column;
                text-align: center;
            }
            
            .welcome-actions {
                margin-top: 20px;
                align-items: center;
            }
            
            .video-grid {
                grid-template-columns: 1fr;
            }
        }
        
        /* Stats Counter */
        .stats-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .stat-card {
            background-color: var(--card-bg);
            border-radius: 8px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
        }
        
        .stat-number {
            font-size: 36px;
            font-weight: bold;
            color: var(--accent-color);
            margin-bottom: 10px;
        }
        
        .stat-label {
            font-size: 14px;
            color: #878787;
        }
        
        /* Modal */
        .modal-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: all 0.3s ease;
        }
        
        .modal-bg.active {
            opacity: 1;
            visibility: visible;
        }
        
        .modal {
            background-color: var(--secondary-color);
            border-radius: 8px;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            box-shadow: 0 5px 25px rgba(0, 0, 0, 0.5);
            position: relative;
        }
        
        .modal-close {
            position: absolute;
            top: 10px;
            right: 10px;
            background: none;
            border: none;
            color: var(--text-color);
            font-size: 20px;
            cursor: pointer;
            z-index: 10;
        }
        
        .modal-video {
            width: 100%;
            max-height: 450px;
            background-color: #000;
        }
        
        .modal-video iframe {
            width: 100%;
            height: 450px;
            border: none;
        }
        
        .modal-content {
            padding: 20px;
        }
        
        .modal-title {
            font-size: 24px;
            margin-bottom: 10px;
        }
        
        .modal-meta {
            display: flex;
            justify-content: space-between;
            margin-bottom: 20px;
            color: #878787;
        }
        
        .modal-description {
            margin-bottom: 20px;
            line-height: 1.6;
        }
        
        .creator-info {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        
        .creator-avatar {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--accent-color);
            margin-right: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--primary-color);
            font-weight: bold;
            font-size: 20px;
        }
        
        .creator-details h4 {
            margin-bottom: 5px;
        }
        
        .creator-details p {
            color: #878787;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <header>
        <div class="header-container">
            <a href="#" class="logo">Secure<span>Hack</span></a>
            <nav>
                <ul>
                    <li><a href="#" class="active">Dashboard</a></li>
                    <li><a href="#">Labs</a></li>
                    <li><a href="#">Challenges</a></li>
                    <li><a href="#">Courses</a></li>
                    <li><a href="#">Community</a></li>
                </ul>
            </nav>
            <div class="user-menu">
                <div class="user-avatar" id="user-avatar">A</div>
                <div class="dropdown-menu" id="dropdown-menu">
                    <ul>
                        <li><a href="#">Profile</a></li>
                        <li><a href="#">My Courses</a></li>
                        <li><a href="#">Settings</a></li>
                        <li class="dropdown-divider"></li>
                        <li><a href="#">Help & Support</a></li>
                        <li><a href="#">Logout</a></li>
                    </ul>
                </div>
            </div>
        </div>
    </header>
    
    <main class="container">
        <section class="welcome-banner">
            <div class="welcome-text">
                <h1>Welcome to SecureHack, Admin!</h1>
                <p>Your cybersecurity journey begins here. Explore our free resources from top cybersecurity mentors to get started.</p>
                <p>Complete your profile to unlock personalized learning paths and track your progress.</p>
            </div>
            <div class="welcome-actions">
                <a href="#" class="btn btn-primary">Complete Profile</a>
                <a href="#" class="btn btn-secondary">Explore Premium</a>
            </div>
        </section>
        
        <section class="stats-section">
            <div class="stats-cards">
                <div class="stat-card">
                    <div class="stat-number">15</div>
                    <div class="stat-label">Free Courses</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">42</div>
                    <div class="stat-label">Practice Labs</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">8</div>
                    <div class="stat-label">Top Mentors</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">28K+</div>
                    <div class="stat-label">Community Members</div>
                </div>
            </div>
        </section>
        
        <section class="content-section">
            <div class="section-header">
                <h2>Top Free Cybersecurity Videos</h2>
                <a href="#" class="view-all">View All <span>→</span></a>
            </div>
            
            <div class="video-grid">
                <!-- Video 1 -->
                <div class="video-card" onclick="openVideoModal('1')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Ethical Hacking Fundamentals">
                        <div class="video-duration">45:22</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">Ethical Hacking Fundamentals: Getting Started</h3>
                        <div class="video-meta">
                            <span>David Mitchell</span>
                            <span>152K views</span>
                        </div>
                        <p class="video-description">Learn the basics of ethical hacking and penetration testing in this comprehensive guide for beginners. No prior experience required.</p>
                        <div class="video-tags">
                            <span class="tag">Ethical Hacking</span>
                            <span class="tag">Beginner</span>
                            <span class="tag">Pentesting</span>
                        </div>
                    </div>
                </div>
                
                <!-- Video 2 -->
                <div class="video-card" onclick="openVideoModal('2')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Web Application Security">
                        <div class="video-duration">38:15</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">OWASP Top 10: Web Application Security Essentials</h3>
                        <div class="video-meta">
                            <span>Sarah Johnson</span>
                            <span>98K views</span>
                        </div>
                        <p class="video-description">Understand the OWASP Top 10 web application vulnerabilities and how to protect against them with practical examples.</p>
                        <div class="video-tags">
                            <span class="tag">Web Security</span>
                            <span class="tag">OWASP</span>
                            <span class="tag">Intermediate</span>
                        </div>
                    </div>
                </div>
                
                <!-- Video 3 -->
                <div class="video-card" onclick="openVideoModal('3')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Network Security">
                        <div class="video-duration">52:41</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">Network Security: From Theory to Practice</h3>
                        <div class="video-meta">
                            <span>Michael Zhang</span>
                            <span>78K views</span>
                        </div>
                        <p class="video-description">A comprehensive guide to securing networks against common attacks and vulnerabilities. Includes practical demonstrations.</p>
                        <div class="video-tags">
                            <span class="tag">Network Security</span>
                            <span class="tag">Firewall</span>
                            <span class="tag">IDS/IPS</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        
        <section class="content-section">
            <div class="section-header">
                <h2>Most Popular Cybersecurity Courses</h2>
                <a href="#" class="view-all">View All <span>→</span></a>
            </div>
            
            <div class="video-grid">
                <!-- Course 1 -->
                <div class="video-card" onclick="openVideoModal('4')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Kali Linux Mastery">
                        <div class="video-duration">10+ hours</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">Kali Linux Mastery: The Complete Ethical Hacking Course</h3>
                        <div class="video-meta">
                            <span>Alex Rodriguez</span>
                            <span>265K views</span>
                        </div>
                        <p class="video-description">Master Kali Linux and learn to use its powerful toolkit for ethical hacking and penetration testing. Hands-on exercises included.</p>
                        <div class="video-tags">
                            <span class="tag">Kali Linux</span>
                            <span class="tag">Ethical Hacking</span>
                            <span class="tag">Full Course</span>
                        </div>
                    </div>
                </div>
                
                <!-- Course 2 -->
                <div class="video-card" onclick="openVideoModal('5')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Cryptography">
                        <div class="video-duration">8+ hours</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">Cryptography and Secure Communications</h3>
                        <div class="video-meta">
                            <span>Emma Wilson</span>
                            <span>124K views</span>
                        </div>
                        <p class="video-description">Understand the principles of modern cryptography, encryption algorithms, and secure communications protocols with practical examples.</p>
                        <div class="video-tags">
                            <span class="tag">Cryptography</span>
                            <span class="tag">Encryption</span>
                            <span class="tag">PKI</span>
                        </div>
                    </div>
                </div>
                
                <!-- Course 3 -->
                <div class="video-card" onclick="openVideoModal('6')">
                    <div class="video-thumbnail">
                        <img src="/api/placeholder/320/180" alt="Malware Analysis">
                        <div class="video-duration">12+ hours</div>
                        <div class="mentor-badge">Top Mentor</div>
                    </div>
                    <div class="video-info">
                        <h3 class="video-title">Malware Analysis Fundamentals</h3>
                        <div class="video-meta">
                            <span>Robert Chen</span>
                            <span>96K views</span>
                        </div>
                        <p class="video-description">Learn techniques for analyzing malicious software, understanding its behavior, and developing effective countermeasures.</p>
                        <div class="video-tags">
                            <span class="tag">Malware</span>
                            <span class="tag">Reverse Engineering</span>
                            <span class="tag">Advanced</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>
    
    <!-- Video Modal -->
    <div class="modal-bg" id="video-modal">
        <div class="modal">
            <button class="modal-close" id="modal-close">×</button>
            <div class="modal-video">
                <iframe id="youtube-embed" src="" frameborder="0" allowfullscreen></iframe>
            </div>
            <div class="modal-content">
                <h2 class="modal-title" id="modal-title">Video Title</h2>
                <div class="modal-meta">
                    <span id="modal-date">March 10, 2025</span>
                    <span id="modal-views">0 views</span>
                </div>
                <div class="creator-info">
                    <div class="creator-avatar" id="creator-initial">D</div>
                    <div class="creator-details">
                        <h4 id="creator-name">Creator Name</h4>
                        <p>Cybersecurity Expert</p>
                    </div>
                </div>
                <div class="modal-description" id="modal-description">
                    Video description goes here.
                </div>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="footer-container">
            <div class="footer-section">
                <h3>SecureHack</h3>
                <ul>
                    <li><a href="#">About Us</a></li>
                    <li><a href="#">Our Team</a></li>
                    <li><a href="#">Careers</a></li>
                    <li><a href="#">Contact</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Resources</h3>
                <ul>
                    <li><a href="#">Blog</a></li>
                    <li><a href="#">Documentation</a></li>
                    <li><a href="#">Community Forum</a></li>
                    <li><a href="#">FAQ</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Legal</h3>
                <ul>
                    <li><a href="#">Terms of Service</a></li>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Cookie Policy</a></li>
                    <li><a href="#">Ethical Guidelines</a></li>
                </ul>
            </div>
            <div class="footer-section">
                <h3>Connect</h3>
                <ul>
                    <li><a href="#">Twitter</a></li>
                    <li><a href="#">LinkedIn</a></li>
                    <li><a href="#">Discord</a></li>
                    <li><a href="#">YouTube</a></li>
                </ul>
            </div>
        </div>
        <div class="footer-bottom">
            <p>© 2025 SecureHack. All rights reserved.</p>
        </div>
    </footer>
    
    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // User dropdown menu
            const userAvatar = document.getElementById('user-avatar');
            const dropdownMenu = document.getElementById('dropdown-menu');
            
            userAvatar.addEventListener('click', function() {
                dropdownMenu.classList.toggle('show');
            });
            
            // Close dropdown when clicking outside
            document.addEventListener('click', function(event) {
                if (!userAvatar.contains(event.target) && !dropdownMenu.contains(event.target)) {
                    dropdownMenu.classList.remove('show');
                }
            });
            
            // Video Modal
            const modalBg = document.getElementById('video-modal');
            const modalClose = document.getElementById('modal-close');
            const youtubeEmbed = document.getElementById('youtube-embed');
            
            modalClose.addEventListener('click', function() {
                modalBg.classList.remove('active');
                youtubeEmbed.src = '';
            });
            
            // Close modal when clicking on background
            modalBg.addEventListener('click', function(event) {
                if (event.target === modalBg) {
                    modalBg.classList.remove('active');
                    youtubeEmbed.src = '';
                }
            });
        });
        
        // Function to open video modal
        function openVideoModal(videoId) {
            const modalBg = document.getElementById('video-modal');
            const youtubeEmbed = document.getElementById('youtube-embed');
            const modalTitle = document.getElementById('modal-title');
            const modalViews = document.getElementById('modal-views');
            const modalDescription = document.getElementById('modal-description');
            const creatorName = document.getElementById('creator-name');
            const creatorInitial = document.getElementById('creator-initial');
            
            // Video data - in a real app, this would come from an API
            const videoData = {
                '1': {
