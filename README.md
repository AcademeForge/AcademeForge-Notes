<html lang="en">
<head>
    <meta name="google-site-verification" content="F1L0xfSoJ09Jp0SjvlmTnzkWK_fuYyhBw36QvRdDGwM" />
    <!-- Moving Banner -->
    <div class="banner-container">
        <marquee behavior="scroll" direction="left">
            Stay Tuned For more updates 
            <a href="https://t.me/AcademeForge" target="_blank" style="color: #ff4081; text-decoration: underline;">Join our Telegram group</a> 🌟
        </marquee>
    </div>

    <!-- Your existing login form here -->
    <div class="login-container">
        <!-- Login form content -->
    </div>

    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
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
        }
        .container {
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 345px rgba(0, 255, 255, 0.5);
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
    </style>
</head>
<body>

<!-- Back Button -->
<button class="back-button" id="backButton" onclick="goBack()">Back</button>

<!-- Login Page -->
<div class="container" id="loginContainer">
    <marquee behavior="scroll" direction="left">
        Welcome to AcademeForge – Something Out Of The Box 🎁!
    </marquee>
    <h2>LOGIN</h2>
    <button class="access-button" onclick="continueAsGuest()">Continue as Guest</button>
</div>

<script>
    // Existing script code...

    function continueAsGuest() {
        showPage('class');
    }

    // Rest of your script...
</script>

<!-- Class Selection Page -->
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
<!-- About Us Container -->
<div id="aboutUsContainer" class="hidden">
    <!-- About Us Button -->
    <button onclick="openAboutUs()" class="option" style="background-color: #ff4081; color: white; width: 90%; margin-top: 20px;">
        About Us
    </button>

    <!-- About Us Pop-up -->
    <div id="aboutUsPopup" class="hidden" style="
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
    ">
        <h2 style="color: #ff4081;">About the Team</h2>
        <p><strong>Devraj Kumar</strong> – Founder & CEO</p>
        <p><strong>Mandeep Boot Jolakiya</strong> – Co-Founder & CEO</p>
        <h3 style="color: #00e5ff;">Special Thanks:</h3>
        <p>We extend our heartfelt gratitude to <strong>Ujjwal</strong>, <strong>Amrit</strong>, <strong>Palak</strong>, <strong>Aadhar Bhattacharya</strong> and <strong>Bhuvam</strong> for their invaluable support in managing our community. Your contributions have made a significant impact!</p>
        <button onclick="closeAboutUs()" class="option" style="background-color: #ff4081; color: white; margin-top: 10px;">Close</button>
    </div>
</div>

<!-- JavaScript to Open and Close Pop-up -->
<script>
    function openAboutUs() {
        document.getElementById('aboutUsPopup').classList.remove('hidden');
    }

    function closeAboutUs() {
        document.getElementById('aboutUsPopup').classList.add('hidden');
    }

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).classList.add('hidden');
        document.getElementById(`${page}Container`).classList.remove('hidden');
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';

        // Show "About Us" button only on login page
        if (page === 'login') {
            document.getElementById('aboutUsContainer').classList.remove('hidden');
        } else {
            document.getElementById('aboutUsContainer').classList.add('hidden');
        }

        currentPage = page;
    }
// Show About Us button when the page initially loads
window.onload = () => {
    showPage('login'); // Ensure the login page is set as default
    document.getElementById('aboutUsButton').style.display = 'block'; // Show About Us button
}
</script>

</body>
</html>


