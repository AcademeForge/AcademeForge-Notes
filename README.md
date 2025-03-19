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
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
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
    <input type="text" id="username" placeholder="username : AF" />
    <input type="password" id="password" placeholder="Password : 2024" />
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
<!-- Class Selection Page -->
<div class="container">
    <h2>Select Your Class</h2>
    <div class="option" onclick="showTimetableSelection()">Class 9</div>
    <div class="option" onclick="showTimetableSelection()">Class 10</div>
    <div class="option" onclick="showTimetableSelection()">Class 11</div>
    <div class="option" onclick="showTimetableSelection()">Class 12</div>
</div>

<!-- Timetable Selection (Appears after class selection) -->
<div class="container hidden" id="timetableSelectionContainer">
    <h2>Select Timetable</h2>
    <div class="option" onclick="showTimetable('regular')">Regular Timetable</div>
    <div class="option" onclick="showTimetable('dummy')">Dummy Timetable</div>
</div>

<!-- Regular Timetable Section -->
<div id="regularTimetable" class="container hidden">
    <h2>Regular Timetable</h2>
    <p><strong>8:00 AM - 2:00 PM: School</strong></p>
    <p><strong>2:00 PM - 3:00 PM: Break</strong></p>
    <p><strong>3:00 PM - 6:00 PM: Study (Subject 1)</strong></p>
    <p><strong>6:00 PM - 7:00 PM: Break</strong></p>
    <p><strong>7:00 PM - 9:00 PM: Study (Subject 2)</strong></p>
    <button class="back-button" onclick="backToTimetableSelection()">Back</button>
</div>

<!-- Dummy Timetable Section -->
<div id="dummyTimetable" class="container hidden">
    <h2>Dummy Timetable</h2>
    <p><strong>9:00 AM - 11:00 AM: Study (Subject 1)</strong></p>
    <p><strong>11:00 AM - 1:00 PM: Study (Subject 2)</strong></p>
    <p><strong>1:00 PM - 2:00 PM: Break</strong></p>
    <p><strong>2:00 PM - 4:00 PM: Study (Subject 3)</strong></p>
    <p><strong>4:00 PM - 6:00 PM: Study (Subject 4)</strong></p>
    <button class="back-button" onclick="backToTimetableSelection()">Back</button>
</div>

<script>
    // Function to show timetable selection after class is selected
    function showTimetableSelection() {
        // Hide class selection and show timetable selection
        document.querySelector('.container').classList.add('hidden');
        document.getElementById('timetableSelectionContainer').classList.remove('hidden');
    }

    // Function to show the correct timetable (Regular or Dummy)
    function showTimetable(type) {
        if (type === 'regular') {
            document.getElementById('regularTimetable').classList.remove('hidden');
            document.getElementById('dummyTimetable').classList.add('hidden');
        } else if (type === 'dummy') {
            document.getElementById('dummyTimetable').classList.remove('hidden');
            document.getElementById('regularTimetable').classList.add('hidden');
        }
    }

    // Function to go back to timetable selection
    function backToTimetableSelection() {
        document.getElementById('regularTimetable').classList.add('hidden');
        document.getElementById('dummyTimetable').classList.add('hidden');
        document.getElementById('timetableSelectionContainer').classList.remove('hidden');
    }
</script>

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
        <p><strong>Aadhar Bhattacharya</strong> – Co-Founder & Lead Educator</p>
        <h3 style="color: #00e5ff;">Special Thanks:</h3>
        <p>We extend our heartfelt gratitude to <strong>Ujjwal</strong>, <strong>Amrit</strong>, <strong>Palak</strong>, and <strong>Bhuvam</strong> for their invaluable support in managing our community. Your contributions have made a significant impact!</p>
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
};
</script>
</body>
</html>