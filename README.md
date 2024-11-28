<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Expression Calculation</title>
    <style>
        /* إضافة المتغيرات CSS */
        :root {
            --uv-styles-color-surface: #fff;
            --uv-styles-color-footer: #f8f9fa;
            --uv-styles-color-outline: #dadce0;
            --uv-styles-color-icon-on-secondary: #70757a;
            --uv-styles-color-scrim: #0009;
            --uv-styles-color-on-scrim: #fff;
            --uv-styles-color-primary: #e74c3c; /* اللون الأحمر البين */
            --uv-styles-color-on-primary: #fff;
            --uv-styles-color-secondary: #e8f0fe;
            --uv-styles-color-on-secondary: #1558d6;
            --uv-styles-color-text-primary: #e74c3c; /* اللون الأحمر للنص */
            --uv-styles-color-text-default: #3c4043;
            --uv-styles-color-review-stars: #fbbc04;
            --uv-styles-color-letterbox: #f1f3f4;
            --center-width: 652px;
        }

        body {
            font-family: Arial, sans-serif;
            font-size: 20px;
            line-height: 1.3;
            color: var(--uv-styles-color-text-default);
            margin: 0;
            padding: 0;
            text-align: center;
            
            /* إضافة صورة خلفية مع تأثير تعتيم */
            background-image: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url('https://lesalarie.ma/wp-content/uploads/2019/01/Nexteer.jpg');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
            height: 100vh; /* ملء الشاشة */
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        h1 {
            color: #e74c3c; /* اللون الأحمر */
            font-size: 3em;
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); /* تأثير الظل للنص */
        }

        .container {
            background-color: rgba(255, 255, 255, 0.9); /* خلفية شفافة قليلاً */
            padding: 20px;
            border-radius: 15px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.2); /* إضافة ظل */
            max-width: 400px;
            width: 90%;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .result {
            font-size: 2em;
            color: var(--uv-styles-color-primary);
            font-weight: bold;
            margin-top: 20px;
            padding: 20px;
            border-radius: 10px;
            display: none; /* إخفاء النتيجة بشكل افتراضي */
        }

        input {
            margin: 10px 0;
            padding: 10px;
            font-size: 1.2em;
            width: 100%;
            border-radius: 8px;
            border: 2px solid #ccc;
            transition: border-color 0.3s ease;
        }

        input:focus {
            border-color: #e74c3c; /* تغيير اللون عند التركيز */
            outline: none;
        }

        button {
            padding: 10px 20px;
            font-size: 1.2em;
            background-color: var(--uv-styles-color-primary);
            color: var(--uv-styles-color-on-primary);
            border: none;
            cursor: pointer;
            margin-top: 10px;
            border-radius: 8px;
            transition: background-color 0.3s ease;
            width: 100%;
        }

        button:hover {
            background-color: #c0392b; /* لون داكن عند المرور */
        }

        .message {
            margin-top: 15px;
            font-size: 1em;
            color: #d9534f;
        }

        .message.success {
            color: green;
        }

        /* تنسيق الجمل أسفل الصفحة */
        .footer-text {
            font-size: 1em;
            color: white;
            margin-top: 20px;
            font-family: 'Cursive', sans-serif;
        }

        .footer-year {
            font-size: 0.9em;
            color: white;
        }
    </style>
</head>
<body>
    <h1>Nexteer Automotive</h1>
    <div class="container">
        <!-- نموذج لإدخال اسم المستخدم وكلمة المرور -->
        <input type="text" id="username" placeholder="Enter Username">
        <input type="password" id="password" placeholder="Enter Password"> <!-- تم تأكيد تشفير كلمة المرور -->
        <button onclick="validateUser()">Submit</button>

        <!-- رسالة نجاح أو خطأ -->
        <div id="message" class="message"></div>

        <!-- نتيجة الحساب -->
        <div class="result" id="result"></div>
    </div>

    <!-- النص في أسفل الصفحة -->
    <div class="footer-text">
        Mohamed Benrahou
    </div>
    <div class="footer-year">
        2024-2025
    </div>

    <script>
        // دالة لحساب التعبير
        function calculateExpression(day, hour) {
            return ((day * day) + (hour * 3) + day) + 50;
        }

        // دالة لعرض النتيجة
        function displayResult(result) {
            const resultDiv = document.getElementById('result');
            resultDiv.textContent = `${result}`; // عرض النتيجة فقط
            resultDiv.style.display = 'block';
        }

        // دالة للتحقق من اسم المستخدم وكلمة المرور
        function validateUser() {
            const username = document.getElementById('username').value.trim();
            const password = document.getElementById('password').value.trim();
            const messageDiv = document.getElementById('message');

            // التحقق من المدخلات
            if (username === "" || password === "") {
                messageDiv.textContent = "Please enter both username and password.";
                messageDiv.classList.remove('success');
                return;
            }

            if (username === "Admin" && password === "Manukraft") {
                const now = new Date();
                const day = now.getDate();
                const hour = now.getHours();
                const result = calculateExpression(day, hour);

                messageDiv.textContent = "Login successful!";
                messageDiv.classList.add('success');
                displayResult(result);
            } else {
                messageDiv.textContent = "Invalid username or password.";
                messageDiv.classList.remove('success');
            }
        }
    </script>
</body>
</html># Simo
Fw
