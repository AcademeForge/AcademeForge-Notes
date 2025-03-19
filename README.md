
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AcademeForge - Login</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            margin: 0;
            padding: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            color: #fff;
        }
        .login-container {
            text-align: center;
            background: rgba(0,0,0,0.6);
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.3);
            animation: fadeIn 1.2s ease;
        }
        h1 {
            font-size: 28px;
            margin-bottom: 20px;
        }
        .login-input {
            padding: 12px;
            width: 80%;
            margin-bottom: 10px;
            border: 2px solid #ff9a9e;
            border-radius: 25px;
            outline: none;
            transition: 0.3s;
            background: #fff;
            color: #333;
        }
        .login-input:focus {
            border-color: #fad0c4;
            box-shadow: 0 0 10px rgba(255, 154, 158, 0.6);
        }
        .login-btn {
            padding: 12px;
            width: 80%;
            background-color: #ff9a9e;
            color: white;
            border: none;
            border-radius: 25px;
            cursor: pointer;
            font-size: 16px;
            transition: background 0.3s;
        }
        .login-btn:hover {
            background-color: #fad0c4;
        }
        .countdown {
            display: none;
            font-size: 24px;
            font-weight: bold;
            margin-top: 20px;
            color: #ffcccb;
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
    <input type="text" class="login-input" placeholder="Enter Code" />
    <button class="login-btn" onclick="startCountdown()">Login</button>
    <div class="countdown" id="countdown"></div>
</div>

<script>
    function startCountdown() {
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
</html>

    <div>
        <select id="class" onchange="showStreams()">
            <option value="">Select Class</option>
            <option value="9">Class 9</option>
            <option value="10">Class 10</option>
            <option value="11">Class 11</option>
            <option value="12">Class 12</option>
        </select>

        <div id="stream-section" style="display:none;">
            <select id="stream" onchange="showSubjects()">
                <option value="">Select Stream</option>
                <option value="science">Science</option>
                <option value="commerce">Commerce</option>
                <option value="arts">Arts</option>
            </select>
        </div>

        <div id="subjects-section" class="subjects"></div>
    </div>
</div>

<script>
    const subjectLinks = {
        "9": {
            "English": "#",
            "Hindi": "#",
            "Math": "#",
            "Science": "#",
            "Social Science": "#"
        },
        "10": {
            "English": "#",
            "Hindi": "#",
            "Math": "#",
            "Science": "#",
            "Social Science": "#"
        },
        "11": {
            "science": {
                "Biology": "#",
                "Math": "#",
                "Physics": "#",
                "Chemistry": "#"
            },
            "commerce": {
                "Business Studies": "#",
                "Accountancy": "#",
                "Economics": "#"
            },
            "arts": {
                "History": "#",
                "Political Science": "#",
                "Economics": "#",
                "Psychology": "#",
                "Geography": "#"
            }
        },
        "12": {
            "science": {
                "Biology": "#",
                "Math": "#",
                "Physics": "#",
                "Chemistry": "#"
            },
            "commerce": {
                "Business Studies": "#",
                "Accountancy": "#",
                "Economics": "#"
            },
            "arts": {
                "History": "#",
                "Political Science": "#",
                "Economics": "#",
                "Psychology": "https://drive.google.com/drive/folders/11Y7G9_79zt197nQFMYgKpsKcAb99Ge7c",
                "Geography": "#"
            }
        }
    };

    function login() {
        alert("Login Successful");
    }

    function showStreams() {
        const selectedClass = document.getElementById("class").value;
        const streamSection = document.getElementById("stream-section");
        const subjectsSection = document.getElementById("subjects-section");

        streamSection.style.display = selectedClass === "11" || selectedClass === "12" ? "block" : "none";
        subjectsSection.style.display = selectedClass === "9" || selectedClass === "10" ? "block" : "none";

        if (selectedClass === "9" || selectedClass === "10") {
            displaySubjects(subjectLinks[selectedClass]);
        }
    }

    function showSubjects() {
        const selectedClass = document.getElementById("class").value;
        const selectedStream = document.getElementById("stream").value;
        if (selectedClass === "11" || selectedClass === "12") {
            displaySubjects(subjectLinks[selectedClass][selectedStream]);
        }
    }

    function displaySubjects(subjects) {
        const subjectsSection = document.getElementById("subjects-section");
        subjectsSection.innerHTML = "";

        if (subjects) {
            for (const subject in subjects) {
                const btn = document.createElement("button");
                btn.textContent = subject;
                btn.classList.add("subject-btn");
                btn.onclick = () => window.open(subjects[subject], "_blank");
                subjectsSection.appendChild(btn);
            }
            subjectsSection.style.display = "block";
        }
    }
</script>

</body>
</html>