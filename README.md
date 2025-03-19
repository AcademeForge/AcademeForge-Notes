<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AcademeForge - Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #87CEEB, #4682B4);
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
        }
        .login-container {
            background: rgba(0, 0, 0, 0.7);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            animation: fadeIn 1.2s ease;
            width: 90%;
            max-width: 400px;
        }
        h1 {
            font-size: 28px;
            margin-bottom: 20px;
        }
        .login-input {
            padding: 12px;
            width: 80%;
            margin-bottom: 10px;
            border: 2px solid #4682B4;
            border-radius: 25px;
            background: #fff;
            color: #333;
            font-size: 16px;
            outline: none;
            transition: 0.3s;
        }
        .login-input:focus {
            border-color: #ff4500;
            box-shadow: 0 0 10px rgba(255, 69, 0, 0.5);
        }
        .login-btn {
            padding: 12px;
            width: 80%;
            background-color: #4682B4;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            transition: background 0.3s;
        }
        .login-btn:hover {
            background-color: #ff4500;
        }
        .countdown {
            display: none;
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
            color: #ff4500;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

<div class="login-container">
    <h1>Welcome to AcademeForge</h1>
    <input type="text" id="login-code" class="login-input" placeholder="Enter Code" />
    <button class="login-btn" onclick="startCountdown()">Login</button>
    <div class="countdown" id="countdown"></div>
</div>

<script>
    function startCountdown() {
        const code = document.getElementById('login-code').value;
        if (code !== '2024') {
            alert('Invalid Code!');
            return;
        }

        const countdownElement = document.getElementById('countdown');
        let count = 3;
        countdownElement.style.display = 'block';
        countdownElement.innerHTML = count;

        const timer = setInterval(() => {
            count--;
            countdownElement.innerHTML = count;
            if (count === 0) {
                clearInterval(timer);
                window.location.href = "class-selection.html";
            }
        }, 1000);
    }
</script>

</body>


<!-- Back Button -->
<button class="back-button" id="backButton" onclick="goBack()">Back</button>

<!-- Login Page -->
<div class="container" id="loginContainer">
    <h2>LOGIN</h2>
    <input type="text" id="username" placeholder="Username" />
    <input type="password" id="password" placeholder="Password" />
    <button onclick="login()">Sign In</button>
</div>

<!-- Class Selection Page -->
<div class="container hidden" id="classContainer">
    <h2>Select Your Class</h2>
    <div class="option" onclick="selectClass(9)">Class 9</div>
    <div class="option" onclick="selectClass(10)">Class 10</div>
    <div class="option" onclick="selectClass(11)">Class 11</div>
    <div class="option" onclick="selectClass(12)">Class 12</div>
</div>

<!-- Stream Selection Page -->
<div class="container hidden" id="streamContainer">
    <h2>Select Your Stream</h2>
    <div class="option" onclick="selectStream('Science')">Science</div>
    <div class="option" onclick="selectStream('Commerce')">Commerce</div>
    <div class="option" onclick="selectStream('Arts')">Arts</div>
</div>

<!-- Subjects Page -->
<div class="container hidden" id="subjectContainer">
    <h2>Subjects</h2>
    <div id="subjectsList"></div>
</div>

<script>
    let currentPage = 'login';
    let selectedClass = null;
    let selectedStream = null;

    // Define subject links for all classes and streams (PLACEHOLDERS)
    const subjectLinks = {
        9: {
            "Science": "#", 
            "Math": "#", 
            "Social Science": "#", 
            "English": "#", 
            "Hindi": "#" 
        },
        10: {
            "Science": "#", 
            "Math": "#", 
            "Social Science": "#", 
            "English": "#", 
            "Hindi": "#" 
        },
        11: {
            "Science": {
                "Physics": "#", 
                "Chemistry": "#", 
                "Math": "#", 
                "Biology": "#" 
            },
            "Commerce": {
                "Business Studies": "#", 
                "Accountancy": "#", 
                "Economics": "#" 
            },
            "Arts": {
                "History": "#", 
                "Political Science": "#", 
                "Economics": "#", 
                "Psychology": "#", 
                "Geography": "#"
            }
        },
        12: {
            "Science": {
                "Physics": "#", 
                "Chemistry": "#", 
                "Math": "#", 
                "Biology": "#" 
            },
            "Commerce": {
                "Business Studies": "#", 
                "Accountancy": "#", 
                "Economics": "#" 
            },
            "Arts": {
                "History": "#", 
                "Political Science": "#", 
                "Economics": "#", 
                "Psychology": "https://drive.google.com/drive/folders/11Y7G9_79zt197nQFMYgKpsKcAb99Ge7c", 
                "Geography": "#"
            }
        }
    };

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).classList.add('hidden');
        document.getElementById(`${page}Container`).classList.remove('hidden');
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';
        currentPage = page;
    }

    function login() {
        showPage('class');
    }

    function selectClass(cls) {
        selectedClass = cls;
        if (cls <= 10) {
            loadSubjects(cls);
        } else {
            showPage('stream');
        }
    }

    function selectStream(stream) {
        selectedStream = stream;
        loadSubjects(selectedClass);
    }

    function loadSubjects(cls) {
        const subjectsList = document.getElementById('subjectsList');
        subjectsList.innerHTML = '';

        if (cls <= 10) {
            for (const [subject, link] of Object.entries(subjectLinks[cls])) {
                subjectsList.innerHTML += `
                    <div class="option">
                        ${subject}
                        <button class="access-button" onclick="window.open('${link}', '_blank')">Access to Notes</button>
                    </div>
                `;
            }
        } else {
            for (const [subject, link] of Object.entries(subjectLinks[cls][selectedStream])) {
                subjectsList.innerHTML += `
                    <div class="option">
                        ${subject}
                        <button class="access-button" onclick="window.open('${link}', '_blank')">Access to Notes</button>
                    </div>
                `;
            }
        }
        showPage('subject');
    }

    function goBack() {
        if (currentPage === 'subject') showPage(selectedClass > 10 ? 'stream' : 'class');
        else if (currentPage === 'stream') showPage('class');
        else if (currentPage === 'class') showPage('login');
    }
</script>

</body>
</html>