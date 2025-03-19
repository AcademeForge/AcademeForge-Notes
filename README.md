
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
        .option, .access-button, .back-button {
            background-color: #292929;
            color: white;
            padding: 12px;
            margin: 8px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
            width: 90%;
            display: inline-block;
        }
        .option:hover, .access-button:hover, .back-button:hover {
            background-color: #00e5ff;
            color: black;
        }
        .hidden {
            display: none;
        }
        .back-button {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            z-index: 10;
            display: none;
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
    let selectedStream = null;

    // Define subject links for all classes and streams
    const subjectLinks = {
        9: {
            "Science": "https://drive.google.com/drive/folders/1-CtgsAx1kXo67-UUf6HsBunPIgm8FgUl",
            "Math": "https://drive.google.com/drive/folders/1-DH3yoNSnF0iFSIH2CsGGf5RobYwYKyp",
            "Social Science": "https://drive.google.com/drive/folders/1-Dm4Tg6UIlYBiNqGYOYAWZvJExikh7my",
            "English": "https://drive.google.com/drive/folders/1-Gd2i8_7ylzy-gM_sFQMGrtDbiE70vRr",
            "Hindi": "https://drive.google.com/drive/folders/1-EHtC6OQMkNE3qEU5JgPggm5I4ggUWf9"
        },
        10: {
            "Science": "https://drive.google.com/drive/folders/1-bVnCZbCabVmNGCxJ0gY4-FP4BwN9F02",
            "Math": "https://drive.google.com/drive/folders/1-Z7LCbOvKhHvMxqXS3W4qVcAukPVmhXK",
            "Social Science": "https://drive.google.com/drive/folders/1-c9q3sV8BCZjtch0WqWnXnJWSE1il5uS",
            "English": "https://drive.google.com/drive/folders/1-VKypMW3rybYR_0dPrro1JscD8eGtj9u",
            "Hindi": "https://drive.google.com/drive/folders/1-Ud6Gv65aE25yPcul3cbprGvXZrXX2O0"
        },
        11: {
            "Science": {
                "Physics": "https://drive.google.com/drive/folders/100rYQz_YiMNnT7zK_dxW-t8PUYj7GABP",
                "Chemistry": "https://drive.google.com/drive/folders/1-lL_2Z5_4cvklYRMSv2vTWorip9w-RWx",
                "Math": "https://drive.google.com/drive/folders/1-yiJhKx6TVLZQ9DlHyvQLZli8N8Qd6TB",
                "Biology": "https://drive.google.com/drive/folders/1-lL_2Z5_4cvklYRMSv2vTWorip9w-RWx"
            },
            "Commerce": {
                "Business Studies": "#",
                "Accountancy": "#",
                "Economics": "#"
            },
            "Arts": {
                "History": "#",
                "Political Science": "#",
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

        if (cls > 10 && subjectLinks[cls][selectedStream]) {
            for (const [subject, link] of Object.entries(subjectLinks[cls][selectedStream])) {
                subjectsList.innerHTML += `
                    <div class="option">
                        ${subject}
                        <button class="access-button" onclick="window.open('${link}', '_blank')">Access to Notes</button>
                    </div>
                `;
            }
            showPage('subject');
        }
    }

    function goBack() {
        if (currentPage === 'subject') showPage(selectedClass > 10 ? 'stream' : 'class');
        else if (currentPage === 'stream') showPage('class');
        else if (currentPage === 'class') showPage('login');
    }
</script>

</body>
</html>