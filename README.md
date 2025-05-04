<html lang="en">
<head>
    <meta name="google-site-verification" content="F1L0xfSoJ09Jp0SjvlmTnzkWK_fuYyhBw36QvRdDGwM" />
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>AcademeForge</title>

    <!-- Styling for the entire page -->
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
            flex-direction: column;
            overflow: hidden;
        }

        /* Neumorphic Login Box */
        .neumorphic {
            background: #e0e5ec;
            border-radius: 20px;
            box-shadow: 10px 10px 20px #a3b1c6, -10px -10px 20px #ffffff;
            padding: 30px;
            width: 300px;
            text-align: center;
        }

        .neumorphic h1 {
            font-size: 28px;
            color: #ff4081;
            margin-bottom: 20px;
        }

        .neumorphic-input {
            margin: 10px 0;
            padding: 10px;
            width: 100%;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            background: #e0e5ec;
            box-shadow: inset 5px 5px 10px #a3b1c6, inset -5px -5px 10px #ffffff;
            transition: box-shadow 0.3s ease;
        }

        .neumorphic-input:focus {
            box-shadow: inset 5px 5px 10px #a3b1c6, inset -5px -5px 10px #ffffff, 0 0 8px rgba(0, 255, 255, 0.7);
            outline: none;
        }

        .neumorphic-button {
            margin-top: 15px;
            padding: 10px;
            width: 100%;
            border: none;
            border-radius: 8px;
            background-color: #00e5ff;
            color: white;
            font-size: 16px;
            cursor: pointer;
            box-shadow: inset 5px 5px 10px #a3b1c6, inset -5px -5px 10px #ffffff;
            transition: box-shadow 0.3s ease;
        }

        .neumorphic-button:hover {
            box-shadow: inset 10px 10px 20px #a3b1c6, inset -10px -10px 20px #ffffff;
            background-color: #ff4081;
        }

        /* Banner Section */
        .banner-container {
            background-color: #ffcc00;
            padding: 10px;
            color: #000;
            font-size: 16px;
            font-weight: bold;
            text-align: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 9999;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        marquee {
            font-size: 18px;
            font-weight: bold;
            z-index: 10;
        }

        /* Class & Subject Selection Styling */
        .option {
            margin: 15px;
            padding: 20px;
            background-color: #2c2c2c;
            color: white;
            border-radius: 10px;
            font-size: 18px;
            text-align: center;
            cursor: pointer;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s ease, background-color 0.3s ease;
        }

        .option:hover {
            transform: scale(1.05);
            background-color: #00e5ff;
        }

        .container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
        }

        /* Mobile Friendly Styles */
        @media (max-width: 768px) {
            body {
                padding: 10px;
                overflow: auto;
            }

            .neumorphic {
                width: 90%;
                padding: 20px;
            }

            .neumorphic-button {
                font-size: 14px;
            }

            .option {
                width: 80%;
                margin: 10px 0;
                font-size: 16px;
            }
        }
    </style>
</head>
<body>

<!-- Banner Section -->
<div class="banner-container">
    <marquee behavior="scroll" direction="left">
        Stay Tuned For more updates
        <a href="https://t.me/AcademeForge" target="_blank" style="color: #ff4081; text-decoration: underline;">Join our Telegram group</a> 🌟
    </marquee>
</div>

<!-- Neumorphic Login Box -->
<div class="neumorphic" id="loginContainer">
    <h1>Login</h1>
    <input type="text" class="neumorphic-input" placeholder="Username" />
    <input type="password" class="neumorphic-input" placeholder="Password" />
    <button class="neumorphic-button" onclick="continueAsGuest()">Continue as Guest</button>
</div>

<!-- Class Selection Page -->
<div class="container hidden" id="classContainer" style="display: none;">
    <h2>Select Your Class</h2>
    <div class="option" onclick="selectClass(1)">Class 1</div>
    <div class="option" onclick="selectClass(2)">Class 2</div>
    <div class="option" onclick="selectClass(3)">Class 3</div>
    <div class="option" onclick="selectClass(4)">Class 4</div>
    <div class="option" onclick="selectClass(5)">Class 5</div>
    <div class="option" onclick="selectClass(6)">Class 6</div>
    <div class="option" onclick="selectClass(7)">Class 7</div>
    <div class="option" onclick="selectClass(8)">Class 8</div>
</div>

<!-- Subjects Page -->
<div class="container hidden" id="subjectContainer" style="display: none;">
    <h2>Subjects</h2>
    <div id="subjectsList"></div>
</div>

<!-- JavaScript to Open and Close Pop-up -->
<script>
    let currentPage = 'login';
    let selectedClass = null;

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).style.display = 'none';
        document.getElementById(`${page}Container`).style.display = 'block';
        currentPage = page;
    }

    function continueAsGuest() {
        showPage('class');
    }

    function selectClass(cls) {
        selectedClass = cls;
        loadSubjects(cls);
    }

    function loadSubjects(cls) {
        const subjectsList = document.getElementById('subjectsList');
        subjectsList.innerHTML = '';

        const subjectLinks = {
            1: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            2: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            3: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            4: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            5: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            6: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            7: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            },
            8: {
                "Hindi Grammar": "#",
                "English Grammar": "#",
                "Math": "#",
                "Science": "#",
                "General Knowledge": "#"
            }
        };

        const links = subjectLinks[cls] || {};
        for (const [subject, link] of Object.entries(links)) {
            subjectsList.innerHTML += `
                <div class="option">
                    ${subject}
                    <button class="access-button" onclick="window.open('${link}', '_blank')">Access Notes</button>
                </div>
            `;
        }
        showPage('subject');
    }

    window.onload = () => {
        showPage('login');
    };
</script>

</body>
</html>