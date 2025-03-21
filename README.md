<html lang="en">
<head>
<!-- Moving Banner -->
<div class="banner-container">
    <marquee behavior="scroll" direction="left">
        🌟 📢 We will start sharing study materials from <b>1st April</b>. Stay tuned! 🚀 
    <a href="https://t.me/AcademeForge" target="_blank" style="color: #ff4081; text-decoration: underline;">Join our Telegram group</a>
🌟
    </marquee>
</div>
<!-- Logo -->
<div class="logo-container">
    <a href="https://ibb.co/23qH49sJ" target="_blank">
        <img src="https://i.ibb.co/k2KvC79Z/IMG-20250320-164334-559.jpg" alt="AcademeForge Logo">
    </a>
</div>

<style>
    /* Logo Styling */
    .logo-container {
        position: fixed;
        top: 120px; /* Adjust this to position it under the banner */
        Right: 10px; /* Positions the logo on the Right side */
        z-index: 9997;
    }

    .logo-container img {
        height: 40px; /* Reduced size */
        width: auto; 
        border-radius: 5px;
    }
</style>

<!-- Your existing login form here -->
<div class="login-container">
    <!-- Login form content -->
</div>

<!-- CSS for styling the banner -->
<style>
    .banner-container {
        background-color: #ffcc00; /* Background color */
        padding: 10px;
        color: #000; /* Text color */
        font-size: 16px;
        font-weight: bold;
        text-align: center;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        z-index: 9999;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1); /* Shadow effect */
    }

    marquee {
        white-space: nowrap;
        overflow: hidden;
        display: inline-block;
    }
</style>

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
        <marquee behavior="scroll" direction="left">
            Welcome to AcademeForge – Building a strong foundation together!
        </marquee>
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
                "Chemistry": "https://drive.google.com/drive/folders/10A46iQRdTn0AJGwBfsZ4TRZ_naTsGcJ2", 
                "Math": "https://drive.google.com/drive/folders/1-yiJhKx6TVLZQ9DlHyvQLZli8N8Qd6TB", 
                "Biology": "https://drive.google.com/drive/folders/1-lL_2Z5_4cvklYRMSv2vTWorip9w-RWx" 
            },
            "Commerce": {
                "Business Studies": "https://drive.google.com/drive/folders/10hbeBCGpwKV8AJlMLN-gkT8ROL-mPJnL", 
                "Accountancy": "https://drive.google.com/drive/folders/10bQ9TYUr2qS3U5rerp5UMyX3qnzF1N2o", 
                "Economics": "https://drive.google.com/drive/folders/10akiwYES3pDVQoPfTHiGJUZ_y9z7J6sx" 
            },
            "Arts": {
                "History": "https://drive.google.com/drive/folders/11HZgkLXZWY391tQnU6mAkyepSHH7BnwD", 
                "Political Science": "https://drive.google.com/drive/folders/11McG2nZBPwTOQivoYRLnuHDrCTaxZfDj", 
                "Economics": "https://drive.google.com/drive/folders/11Mz2f1dukzNn7zqNA8FATyQuvDS3to4Z", 
                "Psychology": "https://drive.google.com/drive/folders/11OHqx9uiW0po8Jb7EqCDOgy_hNpQa8OH", 
                "Geography": "https://drive.google.com/drive/folders/11OHXiJxjOtqmN0yg_TeqUg8hJEU4nkbk"
            }
        },
        12: {
            "Science": {
                "Physics": "https://drive.google.com/drive/folders/10QCZZ78wmLGERWwVoCnQysVOzizeervS", 
                "Chemistry": "https://drive.google.com/drive/folders/10TlsfeqLn5PHarO3rclePp5bg6HBq4K4", 
                "Math": "https://drive.google.com/drive/folders/10OfK1z06vhLqAhPnuYt4w7cN0rZDtbES", 
                "Biology": "https://drive.google.com/drive/folders/10I1sPq0wvSMD8gNtaoFEFFvtQ3fZSDIF" 
            },
            "Commerce": {
                "Business Studies": "https://drive.google.com/drive/folders/114ncGbXaaDS_Uq_jFZ6S8XvUPxGqUomy", 
                "Accountancy": "https://drive.google.com/drive/folders/1133qJ8A91II5MwG9dJMeyQxgF88GEJe6", 
                "Economics": "https://drive.google.com/drive/folders/10zTfWiTZEjnip9jQ4_NQ5D-iKdgC2I8z" 
            },
            "Arts": {
                "History": "https://drive.google.com/drive/folders/11gfrxRKkwZg9yEREvyS06N6zNGH4QFRi", 
                "Political Science": "https://drive.google.com/drive/folders/11c9BDCtzO6OjZumMYlXhklSfwJud5D9z", 
                "Economics": "https://drive.google.com/drive/folders/11jMqr1owMcbXsVci7CgYbyyfWrb3zgtd", 
                "Psychology": "https://drive.google.com/drive/folders/11Y7G9_79zt197nQFMYgKpsKcAb99Ge7c", 
                "Geography": "https://drive.google.com/drive/folders/11XmaUWcoB2JPes05FONuxLtFbDIfSln0"
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
<!-- Announcement Container -->
<div id="announcementContainer" class="hidden">
    <!-- Announcement Button -->
    <button onclick="openAnnouncement()" class="option" style="background-color: #ff9800; color: white; width: 90%; margin-top: 20px;">
        Announcement
    </button>

    <!-- Announcement Pop-up -->
    <div id="announcementPopup" class="hidden" style="
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: #1e1e1e;
        padding: 20px;
        border-radius: 10px;
        box-shadow: 0 0 15px rgba(255, 152, 0, 0.5);
        z-index: 1000;
        width: 90%;
        max-width: 400px;
        text-align: center;
    ">
        <h2 style="color: #ff9800;">📢 Announcement</h2>
        <p>We are excited to start sharing materials from <strong>1st April</strong>! 🚀</p>
        <p>Join our <a href="https://t.me/AcademeForge" target="_blank" style="color: #00e5ff;">Telegram Group</a> for updates.</p>
        <button onclick="closeAnnouncement()" class="option" style="background-color: #ff9800; color: white; margin-top: 10px;">Close</button>
    </div>
</div>

<!-- JavaScript for Announcement Pop-up -->
<script>
    function openAnnouncement() {
        document.getElementById('announcementPopup').classList.remove('hidden');
    }

    function closeAnnouncement() {
        document.getElementById('announcementPopup').classList.add('hidden');
    }

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).classList.add('hidden');
        document.getElementById(`${page}Container`).classList.remove('hidden');
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';

        // Show About Us & Announcement buttons only on login page
        if (page === 'login') {
            document.getElementById('aboutUsContainer').classList.remove('hidden');
            document.getElementById('announcementContainer').classList.remove('hidden');
        } else {
            document.getElementById('aboutUsContainer').classList.add('hidden');
            document.getElementById('announcementContainer').classList.add('hidden');
        }

        currentPage = page;
    }

    // Show buttons when the page initially loads
    window.onload = () => {
        showPage('login');
    };
    </script>
<!-- Chatbox Button -->
<button id="chatbotButton" onclick="toggleChatbot()" style="
    position: fixed;
    bottom: 20px;
    right: 20px;
    background-color: #6200ea;
    color: white;
    border: none;
    border-radius: 50%;
    width: 50px;
    height: 50px;
    font-size: 20px;
    cursor: pointer;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    display: none; /* Initially hidden */
">💬</button>

<!-- Chatbox Window -->
<div id="chatbotContainer" class="hidden" style="
    position: fixed;
    bottom: 80px;
    right: 20px;
    background-color: #1e1e1e;
    width: 300px;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    display: none;
">
    <div style="background-color: #6200ea; padding: 10px; color: white; text-align: center; border-radius: 10px 10px 0 0;">
        📖 AcademeForge Assistant
    </div>
    <div id="chatbotMessages" style="padding: 10px; height: 200px; overflow-y: auto; color: white;"></div>
    
    <!-- Chat Input & Send Button -->
    <div style="display: flex; border-radius: 0 0 10px 10px;">
        <input id="chatbotInput" type="text" placeholder="Ask something..." style="
            flex: 1;
            padding: 8px;
            border: none;
            background-color: #333;
            color: white;
            border-radius: 0 0 0 10px;
        ">
        <button onclick="sendMessage()" style="
            background-color: #6200ea;
            color: white;
            border: none;
            padding: 8px;
            border-radius: 0 0 10px 0;
            cursor: pointer;
        ">📩</button>
    </div>
</div>

<!-- Chatbot Script -->
<script>
    function toggleChatbot() {
        var chatbox = document.getElementById('chatbotContainer');
        chatbox.style.display = (chatbox.style.display === 'none' || chatbox.style.display === '') ? 'block' : 'none';
    }

    function sendMessage() {
        var inputField = document.getElementById('chatbotInput');
        var input = inputField.value.trim().toLowerCase();
        var chatbox = document.getElementById('chatbotMessages');

        if (input === "") return; // Prevent empty messages

        var responses = {
            "notes": "📚 You can find notes in the study material section of your class. Visit AcademeForge for more details!",
            "timetable": "📅 The timetable is available under the 'Timetable' section after selecting your class.",
            "ast": "🎓 AST (AcademeForge Scholars Test) is an exam for students from Class 1 to 10. Visit the AST section for details!",
            "extra study material": "📖 Extra study materials are available in the 'Extra Material' section.",
            "about us": "🏫 AcademeForge is an educational platform founded by Devraj Kumar and co-founded by Aadi & Mandeep.",
            "hello": "👋 Hello! How can I assist you today?",
            "hi": "😊 Hi there! Need help?",
            "bye": "👋 Goodbye! Happy studying!",
            "who is the founder": "🛠 AcademeForge was founded by **Devraj Kumar** and co-founded by **Aadi & Mandeep**.",
            "contact": "📧 You can contact us at **AcademeForge@gmail.com** for any queries.",
            "how to register for ast": "📝 You can register for AST through our official website. Fees and details are mentioned in the AST section.",
            "exam pattern for ast": "📊 The AST exam has 3 rounds: **Preliminary (MCQs), Advanced (Written + MCQs), and Interview**. Full details are on the AST page.",
            "subjects in ast": "🧠 AST covers **Math, Science, English, and General Knowledge**. You can choose up to 4 subjects.",
            "scholarship details": "🏆 Students qualifying in AST Interview Round get **scholarships from ₹500–₹2,000 per month for up to 12 months**.",
            "study material for class 9": "📚 Study materials for Class 9 can be accessed at: [Click Here](https://drive.google.com/drive/folders/1-Gd2i8_7ylzy-gM_sFQMGrtDbiE70vRr)",
            "study material for class 10": "📚 Study materials for Class 10 can be accessed at: [Click Here](https://drive.google.com/drive/folders/1-VKypMW3rybYR_0dPrro1JscD8eGtj9u)",
            "study material for class 11": "📚 Study materials for Class 11 (Science) can be accessed at: [Click Here](https://drive.google.com/drive/folders/1-lL_2Z5_4cvklYRMSv2vTWorip9w-RWx)",
            "study material for class 12": "📚 Study materials for Class 12 will be available soon. Stay tuned!",
            "how to access notes": "📖 You can access notes from the **Study Material** section by selecting your class and subject.",
            "who can participate in ast": "👦👧 Students from **Class 1 to 10** can participate in AST.",
            "how to apply for scholarship": "💰 You need to qualify in AST **Round 3 (Interview)** to get a scholarship.",
            "how to join academeforge": "🔗 You can follow our social media pages and join our community for updates!",
            "who is eligible for ast": "✅ Any student from Class 1 to 10 can appear for AST.",
            "how much is the registration fee for ast": "💰 AST registration fees are **₹70 for regular** and **₹100 for late registration**."
        };

        var response = responses[input] || "❓ I'm not sure about that. Try asking about 'Notes', 'Timetable', 'AST', or 'Scholarships'.";
        
        chatbox.innerHTML += `<p><strong>You:</strong> ${input}</p>`;
        chatbox.innerHTML += `<p><strong>Bot:</strong> ${response}</p>`;

        inputField.value = ""; // Clear input field
        chatbox.scrollTop = chatbox.scrollHeight; // Auto scroll to latest message
    }

    // Allow Enter key to send messages
    document.getElementById('chatbotInput').addEventListener('keypress', function(event) {
        if (event.key === 'Enter') {
            sendMessage();
        }
    });

    // Show Chatbot Button ONLY on the Login Page
    function showPage(page) {
        document.getElementById("chatbotButton").style.display = (page === "login") ? "block" : "none";
        document.getElementById("chatbotContainer").style.display = "none"; // Hide chatbox when changing pages

        // Ensure "About Us" & "Announcement" buttons are visible on login page
        if (page === "login") {
            document.getElementById('aboutUsContainer').classList.remove('hidden');
            document.getElementById('announcementContainer').classList.remove('hidden');
        } else {
            document.getElementById('aboutUsContainer').classList.add('hidden');
            document.getElementById('announcementContainer').classList.add('hidden');
        }
    }

    // Ensure correct elements are visible when the page loads
    window.onload = () => {
        showPage("login"); 
    };
</script>

</body>
</html>