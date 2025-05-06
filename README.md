<html lang="en">  
<head>  
    <meta name="google-site-verification" content="F1L0xfSoJ09Jp0SjvlmTnzkWK_fuYyhBw36QvRdDGwM" />  
    <meta charset="UTF-8" />  
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
    <title>AcademeForge</title>  <!-- Styling for the entire page -->  
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

    .container {  
        background: #1e1e1e;  
        padding: 20px;  
        border-radius: 10px;  
        box-shadow: 0 0 345px rgba(0, 255, 255, 0.5);  
        text-align: center;  
        width: 100%;  
        max-width: 320px;  
        transition: transform 0.3s ease;  
        margin-top: 20px;  
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

    /* Mobile Friendly Styles */  
    @media (max-width: 768px) {  
        body {  
            padding: 10px;  
        }  
        .container {  
            width: 100%;  
            padding: 15px;  
        }  
        .option, .access-button, .back-button {  
            width: 100%;  
            font-size: 14px;  
        }  
        .banner-container {  
            font-size: 14px;  
        }  
    }  
</style>

</head>  
<body>  <!-- Banner Section -->  <div class="banner-container">  
    <marquee behavior="scroll" direction="left">  
        Stay Tuned For more updates  
        <a href="https://t.me/AcademeForge" target="_blank" style="color: #ff4081; text-decoration: underline;">Join our Telegram group</a> 🌟  
    </marquee>  
</div>  <!-- Back Button -->  <button class="back-button" id="backButton" onclick="goBack()">Back</button>

<!-- Login Page -->  <div class="container" id="loginContainer">  
    <marquee behavior="scroll" direction="left">  
        Welcome to AcademeForge – Something Out Of The Box 🎁!  
    </marquee>  
    <h2>LOGIN</h2>  
    <button class="access-button" onclick="continueAsGuest()">Continue as Guest</button>  
</div>  <!-- Class Selection Page -->  <div class="container hidden" id="classContainer">  
    <h2>Select Your Class</h2>  
    <div class="option" onclick="selectClass(1)">Class 1</div>  
    <div class="option" onclick="selectClass(2)">Class 2</div>  
    <div class="option" onclick="selectClass(3)">Class 3</div>  
    <div class="option" onclick="selectClass(4)">Class 4</div>  
    <div class="option" onclick="selectClass(5)">Class 5</div>  
    <div class="option" onclick="selectClass(6)">Class 6</div>  
    <div class="option" onclick="selectClass(7)">Class 7</div>  
    <div class="option" onclick="selectClass(8)">Class 8</div>  
</div>  <!-- Subjects Page -->  <div class="container hidden" id="subjectContainer">  
    <h2>Subjects</h2>  
    <div id="subjectsList"></div>  
</div>  <!-- About Us Container -->  <div id="aboutUsContainer" class="hidden">  
    <!-- About Us Button -->  
    <button onclick="openAboutUs()" class="option" style="background-color: #ff4081; color: white; width: 90%; margin-top: 20px;">  
        About Us  
    </button>  <!-- About Us Pop-up -->  
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

</div>  <!-- JavaScript to Open and Close Pop-up -->  <script>  
    let currentPage = 'login';  
    let selectedClass = null;  
  
    function showPage(page) {  
        document.getElementById(`${currentPage}Container`).classList.add('hidden');  
        document.getElementById(`${page}Container`).classList.remove('hidden');  
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';  
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
</script>  <!-- About Us Container -->  <div id="aboutUsContainer" class="hidden">  
    <!-- About Us Button -->  
    <button onclick="openAboutUs()" class="option" style="background-color: #ff4081; color: white; width: 90%; margin-top: 20px;">  
        About Us  
    </button>  <!-- About Us Pop-up -->  
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

</div>  <!-- JavaScript to Open and Close Pop-up -->  <script>  
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


<div class="container" id="loginContainer">

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
    <input id="chatbotInput" type="text" placeholder="Ask something..." onkeypress="handleChat(event)" style="
        width: 100%;
        padding: 8px;
        border: none;
        border-radius: 0 0 10px 10px;
        background-color: #333;
        color: white;
    ">
</div>

<!-- Chatbot Script -->
<script>
    function toggleChatbot() {
        var chatbox = document.getElementById('chatbotContainer');
        chatbox.style.display = (chatbox.style.display === 'none') ? 'block' : 'none';
    }

    function handleChat(event) {
        if (event.key === 'Enter') {
            var input = document.getElementById('chatbotInput').value.toLowerCase();
            var chatbox = document.getElementById('chatbotMessages');

            const keywordResponses = [
                { keywords: ["notes", "pdf"], response: "You can download notes from the Study Material section. Link: #" },
                { keywords: ["timetable", "time table", "schedule"], response: "The timetable is available here: #. Make sure to check your class group on Telegram too!" },
                { keywords: ["ast", "exam", "test"], response: "AST is the AcademeForge Scholars Test for Classes 1–10. Visit the official page for more details: #" },
                { keywords: ["extra", "material", "resources"], response: "Extra study materials are available here: # in the 'Extra Material' section." },
                { keywords: ["about", "founder", "who is", "what is"], response: "AcademeForge is an educational platform founded by Devraj Kumar and co-founded by Aadi & Mandeep." },
                { keywords: ["class", "join", "enroll"], response: "You can join classes through the AcademeForge portal. Registration link: #" },
                { keywords: ["scholarship"], response: "AST provides scholarship up to ₹5000 to the top rankers. Learn more: #" },
                { keywords: ["certificate"], response: "Certificates are provided to all Round 2 and Round 3 participants of AST." },
                { keywords: ["hello", "hi"], response: "Hello! How can I assist you today?" },
                { keywords: ["bye", "goodbye"], response: "Goodbye! Happy studying with AcademeForge." },
                { keywords: ["contact", "support", "help"], response: "You can reach our team via Instagram or through the contact form on our website: #" },
                { keywords: ["register", "how to register"], response: "You can register for AST from our official form here: #" },
                { keywords: ["price", "fee", "cost"], response: "AST fees are affordable: ₹10 for Round 1, ₹40 for Round 2. Round 3 is free." },
                { keywords: ["round 1"], response: "Round 1 has a ₹10 fee and includes a digital certificate. Top students move to Round 2." },
                { keywords: ["round 2"], response: "Round 2 includes an offline certificate and costs ₹40. Social media shoutouts too!" },
                { keywords: ["round 3"], response: "Round 3 is free and gives medals + scholarship of ₹5000 to top 3 rankers." },
                { keywords: ["telegram", "group"], response: "Join our Telegram group for daily updates and support: #" },
                { keywords: ["academy", "coaching"], response: "We currently provide support materials and quizzes. Coaching classes will be announced soon." },
                { keywords: ["backlog", "pending"], response: "Don’t worry, take one step at a time. You can follow our study plan here: #" },
                { keywords: ["video", "promo", "reel"], response: "Check our latest promo video and reels on Instagram! Follow us: #" }
            ];

            let response = "I'm a small chatbox by AcademeForge. Try asking about: AST, timetable, notes, certificate, extra materials, or scholarship.";

            for (const item of keywordResponses) {
                for (const keyword of item.keywords) {
                    if (input.includes(keyword)) {
                        response = item.response;
                        break;
                    }
                }
                if (response !== "I'm a small chatbox by AcademeForge. Try asking about: AST, timetable, notes, certificate, extra materials, or scholarship.") {
                    break;
                }
            }

            chatbox.innerHTML += `<p><strong>You:</strong> ${input}</p>`;
            chatbox.innerHTML += `<p><strong>Bot:</strong> ${response}</p>`;

            document.getElementById('chatbotInput').value = "";
            chatbox.scrollTop = chatbox.scrollHeight;
        }
    }
</script>

</div>
</script>

  </body>  
</html>