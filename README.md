<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AcademeForge</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #121212;
            color: white;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0,255,255,0.5);
            text-align: center;
            width: 300px;
            transition: transform 0.3s ease;
        }
        h2 {
            color: #ff4081;
        }
        input, button {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
            font-size: 16px;
            outline: none;
        }
        input {
            background: #292929;
            color: white;
        }
        button {
            background: #00e5ff;
            color: black;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        button:hover {
            background: #00bcd4;
        }
        .hidden {
            display: none;
        }
        .option {
            margin: 10px;
            padding: 15px;
            background-color: #292929;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s ease;
        }
        .option:hover {
            background-color: #00e5ff;
            color: black;
        }
        .back-button {
            background: #ff4081;
            color: white;
            padding: 8px 12px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
            display: none;
        }
        .back-button:hover {
            background: #e91e63;
        }
        .access-button {
            background: #ff4081;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
            margin-top: 10px;
        }
        .access-button:hover {
            background: #e91e63;
        }
    </style>
</head>
<body>

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

    const subjectLinks = {
        9: {
            "Science": "https://drive.google.com/drive/folders/1-CtgsAx1kXo67-UUf6HsBunPIgm8FgUl",
            "Math": "https://drive.google.com/drive/folders/1-DH3yoNSnF0iFSIH2CsGGf5RobYwYKyp",
            "Social Science": "https://drive.google.com/drive/folders/1-Dm4Tg6UIlYBiNqGYOYAWZvJExikh7my",
            "English": "https://drive.google.com/drive/folders/1-Gd2i8_7ylzy-gM_sFQMGrtDbiE70vRr",
            "Hindi": "https://drive.google.com/drive/folders/1-EHtC6OQMkNE3qEU5JgPggm5I4ggUWf9"
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
        loadSubjects(selectedClass);
    }

    function loadSubjects(cls) {
        const subjectsList = document.getElementById('subjectsList');
        subjectsList.innerHTML = '';

        if (subjectLinks[cls]) {
            for (const [subject, link] of Object.entries(subjectLinks[cls])) {
                const subjectElement = document.createElement('div');
                subjectElement.classList.add('option');
                subjectElement.innerHTML = `
                    <div>${subject}</div>
                    <button class="access-button" onclick="window.open('${link}', '_blank')">Access to Notes</button>
                `;
                subjectsList.appendChild(subjectElement);
            }
            showPage('subject');
        }
    }

    function goBack() {
        if (currentPage === 'subject') {
            if (selectedClass > 10) {
                showPage('stream');
            } else {
                showPage('class');
            }
        } else if (currentPage === 'stream') {
            showPage('class');
        } else if (currentPage === 'class') {
            showPage('login');
        }
    }
</script>

</body>
</html>