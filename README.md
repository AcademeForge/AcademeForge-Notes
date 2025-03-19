
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AcademeForge</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        .container {
            width: 90%;
            max-width: 400px;
            margin: 20px auto;
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        h2 {
            text-align: center;
            color: #333;
        }
        select, button {
            width: 100%;
            padding: 10px;
            margin-top: 10px;
            border-radius: 4px;
            border: 1px solid #ccc;
            box-sizing: border-box;
        }
        button {
            background-color: #5cb85c;
            color: white;
            border: none;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        button:hover {
            background-color: #4cae4c;
        }
        .subjects {
            margin-top: 20px;
            display: none;
        }
        .subject-btn {
            background-color: #337ab7;
            color: white;
            padding: 10px;
            margin: 5px 0;
            border: none;
            border-radius: 4px;
            width: 100%;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .subject-btn:hover {
            background-color: #286090;
        }
        /* Animated Login */
        .login-container {
            text-align: center;
            margin-top: 30px;
        }
        .login-input {
            padding: 12px;
            width: 80%;
            margin-bottom: 10px;
            border: 2px solid #5cb85c;
            border-radius: 20px;
            outline: none;
            transition: 0.3s ease;
        }
        .login-input:focus {
            border-color: #4cae4c;
            box-shadow: 0 0 10px rgba(92, 184, 92, 0.5);
        }
        .login-btn {
            padding: 12px;
            width: 80%;
            background-color: #5cb85c;
            color: white;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .login-btn:hover {
            background-color: #4cae4c;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>AcademeForge</h2>

    <!-- Animated Login Section -->
    <div class="login-container">
        <input type="text" class="login-input" placeholder="Enter Code" />
        <button class="login-btn" onclick="login()">Login</button>
    </div>

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