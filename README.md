
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta name="google-site-verification" content="F1L0xfSoJ09Jp0SjvlmTnzkWK_fuYyhBw36QvRdDGwM" />
    <title>AcademeForge</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #121212;
            color: white;
            margin: 0;
            padding: 0;
        }

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
        }

        .container {
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 345px rgba(0, 255, 255, 0.5);
            text-align: center;
            width: 90%;
            max-width: 350px;
            margin: 100px auto;
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

        .access-button:hover {
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

        #aboutUsPopup {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
            z-index: 1000;
            width: 90%;
            max-width: 400px;
            text-align: center;
        }
    </style>
</head>
<body>

    <!-- Banner -->
    <div class="banner-container">
        <marquee behavior="scroll" direction="left">
            Stay Tuned For more updates — 
            <a href="https://t.me/AcademeForge" target="_blank" style="color: #ff4081; text-decoration: underline;">Join our Telegram group</a>
        </marquee>
    </div>

    <!-- Back Button -->
    <button class="back-button" id="backButton" onclick="goBack()">Back</button>

    <!-- Login Container -->
    <div class="container" id="loginContainer">
        <marquee behavior="scroll" direction="left">
            Welcome to AcademeForge – Something Out Of The Box 🎁!
        </marquee>
        <h2>LOGIN</h2>
        <button class="access-button" onclick="continueAsGuest()">Continue as Guest</button>
    </div>

    <!-- Class Selection -->
    <div class="container hidden" id="classContainer">
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

    <!-- Subject Selection -->
    <div class="container hidden" id="subjectContainer">
        <h2>Subjects</h2>
        <div id="subjectsList"></div>
    </div>

    <!-- About Us Button + Popup -->
    <div id="aboutUsContainer">
        <button onclick="openAboutUs()" class="option" style="background-color: #ff4081;">About Us</button>

        <div id="aboutUsPopup" class="hidden">
            <h2 style="color: #ff4081;">About the Team</h2>
            <p><strong>Devraj Kumar</strong> – Founder & CEO</p>
            <p><strong>Mandeep Boot Jolakiya</strong> – Co-Founder & CEO</p>
            <h3 style="color: #00e5ff;">Special Thanks:</h3>
            <p>We extend our heartfelt gratitude to <strong>Ujjwal</strong>, <strong>Amrit</strong>, <strong>Palak</strong>, <strong>Aadhar Bhattacharya</strong>, and <strong>Bhuvam</strong> for their invaluable support in managing our community. Your contributions have made a significant impact!</p>
            <button onclick="closeAboutUs()" class="option" style="background-color: #ff4081;">Close</button>
        </div>
    </div>

    <!-- JavaScript -->
    <script>
        let currentPage = 'login';
        let selectedClass = null;
        let selectedStream = null;

        const subjectLinks = {
            1: {
                "Maths": "#",
                "English": "#",
                "EVS": "#"
            },
            2: {
                "Maths": "#",
                "English": "#",
                "EVS": "#"
            },
            // Add more links for other classes...
        };

        function showPage(page) {
            document.getElementById(`${currentPage}Container`).classList.add('hidden');
            document.getElementById(`${page}Container`).classList.remove('hidden');
            document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';

            if (page === 'login') {
                document.getElementById('aboutUsContainer').classList.remove('hidden');
            } else {
                document.getElementById('aboutUsContainer').classList.add('hidden');
            }

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

        function goBack() {
            if (currentPage === 'subject') showPage('class');
            else if (currentPage === 'class') showPage('login');
        }

        function openAboutUs() {
            document.getElementById('aboutUsPopup').classList.remove('hidden');
        }

        function closeAboutUs() {
            document.getElementById('aboutUsPopup').classList.add('hidden');
        }

        window.onload = () => {
            showPage('login');
        };
    </script>
</body>
</html>