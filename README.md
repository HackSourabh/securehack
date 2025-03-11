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
