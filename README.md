
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
        .login-container, .class-container, .stream-container, .subject-container {
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
        .class-option, .stream-option {
            margin: 10px;
            padding: 15px;
            background-color: #292929;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s ease;
        }
        .class-option:hover, .stream-option:hover {
            background-color: #00e5ff;
            color: black;
        }
        .subject-card {
            background-color: #292929;
            margin: 10px 0;
            padding: 10px;
            border-radius: 5px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
            transition: transform 0.3s ease;
        }
        .subject-card img {
            width: 100%;
            border-radius: 5px;
            margin-bottom: 10px;
        }
        .access-button {
            background: #ff4081;
            color: white;
            padding: 10px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .access-button:hover {
            background: #e91e63;
        }
    </style>
</head>
<body>

<!-- Login Page -->
<div class="login-container" id="loginContainer">
    <h2>LOGIN</h2>
    <input type="text" id="username" placeholder="Username" />
    <input type="password" id="password" placeholder="Password" />
    <button onclick="login()">Sign In</button>
</div>

<!-- Class Selection Page -->
<div class="class-container hidden" id="classContainer">
    <h2>Select Your Class</h2>
    <div class="class-option" onclick="selectClass(9)">Class 9</div>
    <div class="class-option" onclick="selectClass(10)">Class 10</div>
    <div class="class-option" onclick="selectClass(11)">Class 11</div>
    <div class="class-option" onclick="selectClass(12)">Class 12</div>
</div>

<!-- Stream Selection Page -->
<div class="stream-container hidden" id="streamContainer">
    <h2>Select Your Stream</h2>
    <div class="stream-option" onclick="selectStream('Science')">Science</div>
    <div class="stream-option" onclick="selectStream('Commerce')">Commerce</div>
    <div class="stream-option" onclick="selectStream('Arts')">Arts</div>
</div>

<!-- Subjects Page -->
<div class="subject-container hidden" id="subjectContainer">
    <h2>Subjects</h2>
    <div id="subjectsList"></div>
</div>

<script>
    function login() {
        // Allow any login and proceed
        document.getElementById('loginContainer').classList.add('hidden');
        document.getElementById('classContainer').classList.remove('hidden');
    }

    function selectClass(classNumber) {
        if (classNumber === 11 || classNumber === 12) {
            document.getElementById('classContainer').classList.add('hidden');
            document.getElementById('streamContainer').classList.remove('hidden');
        } else {
            loadSubjects(classNumber);
        }
    }

    function selectStream(stream) {
        loadSubjects(stream);
    }

    function loadSubjects(selection) {
        document.getElementById('streamContainer').classList.add('hidden');
        document.getElementById('classContainer').classList.add('hidden');
        document.getElementById('subjectContainer').classList.remove('hidden');

        let subjects = [];
        if (selection === 9 || selection === 10) {
            subjects = ["Science", "Math", "Social Science", "English", "Hindi"];
        } else if (selection === "Science") {
            subjects = ["Physics", "Chemistry", "Math", "Biology", "Computer Science"];
        } else if (selection === "Commerce") {
            subjects = ["Business Studies", "Accountancy", "Economics", "Math", "English"];
        } else if (selection === "Arts") {
            subjects = ["History", "Political Science", "Geography", "Economics", "Psychology"];
        }

        let subjectsList = document.getElementById('subjectsList');
        subjectsList.innerHTML = "";

        subjects.forEach(subject => {
            let card = document.createElement('div');
            card.classList.add('subject-card');

            let img = document.createElement('img');
            img.src = `https://source.unsplash.com/300x200/?${subject}`; // AI-like generated image
            img.alt = subject;

            let title = document.createElement('h3');
            title.innerText = subject;

            let button = document.createElement('button');
            button.classList.add('access-button');
            button.innerText = 'Access to Notes';
            button.onclick = () => alert(`Link for ${subject} coming soon!`);

            card.appendChild(img);
            card.appendChild(title);
            card.appendChild(button);

            subjectsList.appendChild(card);
        });
    }
</script>

</body>
</html>