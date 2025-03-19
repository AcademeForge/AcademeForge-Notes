
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
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
        .container {
            background: rgba(0, 0, 0, 0.7);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            width: 90%;
            max-width: 400px;
            animation: fadeIn 1.2s ease;
        }
        .hidden {
            display: none;
        }
        h2 {
            margin-bottom: 20px;
            font-size: 24px;
        }
        input, button {
            padding: 12px;
            width: 80%;
            margin-bottom: 12px;
            border: none;
            border-radius: 25px;
            font-size: 16px;
            outline: none;
        }
        input {
            background: #fff;
            color: #333;
            border: 2px solid #4682B4;
            transition: border-color 0.3s;
        }
        input:focus {
            border-color: #ff4500;
            box-shadow: 0 0 10px rgba(255, 69, 0, 0.5);
        }
        button {
            background-color: #4682B4;
            color: white;
            cursor: pointer;
            transition: background 0.3s;
        }
        button:hover {
            background-color: #ff4500;
        }
        .option {
            padding: 12px;
            background-color: #4682B4;
            color: white;
            border-radius: 25px;
            margin: 5px 0;
            cursor: pointer;
            transition: background 0.3s;
        }
        .option:hover {
            background-color: #ff4500;
        }
        .back-button {
            padding: 10px;
            background-color: #ff4500;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            position: absolute;
            top: 20px;
            left: 20px;
            display: none;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</head>
<body>

<!-- Back Button -->
<button class="back-button" id="backButton" onclick="goBack()">Back</button>

<!-- Login Page -->
<div class="container" id="loginContainer">
    <h2>LOGIN</h2>
    <input type="text" id="login-code" placeholder="Enter Code" />
    <button onclick="startCountdown()">Sign In</button>
    <div class="countdown" id="countdown" style="display: none;"></div>
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

    const subjectLinks = {
        9: {
            "Science": "#", "Math": "#", "Social Science": "#", "English": "#", "Hindi": "#"
        },
        10: {
            "Science": "#", "Math": "#", "Social Science": "#", "English": "#", "Hindi": "#"
        },
        11: {
            "Science": { "Physics": "#", "Chemistry": "#", "Math": "#", "Biology": "#" },
            "Commerce": { "Business Studies": "#", "Accountancy": "#", "Economics": "#" },
            "Arts": { "History": "#", "Political Science": "#", "Economics": "#", "Psychology": "#", "Geography": "#" }
        },
        12: {
            "Science": { "Physics": "#", "Chemistry": "#", "Math": "#", "Biology": "#" },
            "Commerce": { "Business Studies": "#", "Accountancy": "#", "Economics": "#" },
            "Arts": { "History": "#", "Political Science": "#", "Economics": "#", "Psychology": "#", "Geography": "#" }
        }
    };

    function startCountdown() {
        const code = document.getElementById('login-code').value;
        if (code !== '2024') {
            alert('Invalid Code!');
            return;
        }

        let count = 3;
        const countdown = document.getElementById('countdown');
        countdown.style.display = 'block';
        countdown.innerText = count;

        const timer = setInterval(() => {
            count--;
            countdown.innerText = count;
            if (count === 0) {
                clearInterval(timer);
                showPage('class');
            }
        }, 1000);
    }

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).classList.add('hidden');
        document.getElementById(`${page}Container`).classList.remove('hidden');
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';
        currentPage = page;
    }

    function selectClass(cls) {
        selectedClass = cls;
        cls <= 10 ? loadSubjects(cls) : showPage('stream');
    }

    function selectStream(stream) {
        selectedStream = stream;
        loadSubjects(selectedClass);
    }

    function loadSubjects(cls) {
        const subjectsList = document.getElementById('subjectsList');
        subjectsList.innerHTML = '';
        const subjects = cls <= 10 ? subjectLinks[cls] : subjectLinks[cls][selectedStream];
        for (const [subject, link] of Object.entries(subjects)) {
            subjectsList.innerHTML += `<div class="option">${subject}
                <button onclick="window.open('${link}', '_blank')">Access Notes</button></div>`;
        }
        showPage('subject');
    }

    function goBack() {
        currentPage === 'subject' ? (selectedClass > 10 ? showPage('stream') : showPage('class')) :
        currentPage === 'stream' ? showPage('class') : showPage('login');
    }
</script>

</body>
</html>