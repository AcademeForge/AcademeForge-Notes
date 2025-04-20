<html lang="en">
<head>
<meta name="google-site-verification" content="F1L0xfSoJ09Jp0SjvlmTnzkWK_fuYyhBw36QvRdDGwM" />
<!-- Moving Banner -->
<div class="banner-container">
    <marquee behavior="scroll" direction="left">
        Stay Tuned For more updates 
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


<div class="container" id="loginContainer">
  <marquee behavior="scroll" direction="left">
    Welcome to AcademeForge – Something Out Of The Box!
  </marquee>
  <h2>LOGIN</h2>
  <input type="email" id="email" placeholder="Enter your Gmail" class="animate-input" />
  <button onclick="sendOtp()">Send OTP</button>
  <div id="otpSection" style="display:none;">
    <input type="text" id="otp" placeholder="Enter OTP" class="animate-input" />
    <button onclick="verifyOtp()">Verify OTP</button>
  </div>
  <p id="error"></p>
</div>

<!-- Firebase SDKs -->
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>

<script>
  // Firebase configuration (replace with your own Firebase project's details)
  const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
  };

  // Initialize Firebase
  const app = firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();

  function sendOtp() {
    const email = document.getElementById("email").value;
    const error = document.getElementById("error");

    if (!email) {
      error.style.display = 'block';
      error.innerText = "Please enter your Gmail!";
      return;
    }

    // Create a phone number (for testing purposes, use a number linked with your Firebase)
    const phoneNumber = "+1234567890"; // Dummy number for Firebase testing

    // Send OTP
    const appVerifier = new firebase.auth.RecaptchaVerifier('sendOtp', {
      size: 'invisible',
      callback: function(response) {
        // reCAPTCHA solved - can proceed with OTP sending
      }
    });

    auth.signInWithPhoneNumber(phoneNumber, appVerifier)
      .then((confirmationResult) => {
        window.confirmationResult = confirmationResult;
        document.getElementById("otpSection").style.display = "block";
        error.style.display = 'none';
      })
      .catch((error) => {
        error.style.display = 'block';
        error.innerText = "Error sending OTP. Please try again!";
      });
  }

  function verifyOtp() {
    const otp = document.getElementById("otp").value;
    const error = document.getElementById("error");

    if (!otp) {
      error.style.display = 'block';
      error.innerText = "Please enter OTP!";
      return;
    }

    window.confirmationResult.confirm(otp)
      .then((result) => {
        const user = result.user;
        alert("Login Successful!");
        // Redirect or load the user dashboard
      })
      .catch((error) => {
        error.style.display = 'block';
        error.innerText = "Invalid OTP. Please try again!";
      });
  }
</script

    
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
        <p>AcademeForge Scholars Test (AST) 2025 registrations open soon for <strong>Classes 1 to 10</strong>! 🚀</p>
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

<!-- Flashcard Button -->
<button id="flashcardButton" class="option" onclick="openFlashcardPopup()" style="background-color: #3498db; color: white; width: 90%; margin-top: 20px;">
    Social Profiles
</button>
<!-- Flashcard Popup -->
<div id="flashcardPopup" class="hidden" style="
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: #1e1e1e;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 15px rgba(52, 152, 219, 0.5);
    z-index: 1000;
    width: 90%;
    max-width: 400px;
    text-align: center;
    display: none;
">
    <h2 style="color: #3498db;">Social Profiles </h2>

    <div class="card" onclick="flipCard(this)" style="
        background-color: #3498db; 
        color: white; 
        padding: 10px; 
        margin: 10px 0;
        border-radius: 5px;
        cursor: pointer;

     ">
        <div class="card-front">YouTube</div>
        <div class="card-back" style="display: none;"><p>Join our <a href="https://youtube.com/@academeforgepro?si=d6ZmWYKcaFYCrspI" target="_blank" style="color: #00e5ff;">YouTube Channel</a> for updates.</p></div>
    </div>

    <div class="card" onclick="flipCard(this)" style="
        background-color: #3498db; 
        color: white; 
        padding: 10px; 
        margin: 10px 0;
        border-radius: 5px;
        cursor: pointer;
    ">
        <div class="card-front">Instagram</div>
        <div class="card-back" style="display: none;"><p>Follow us on <a href="https://www.instagram.com/academeforgee?igsh=MWYzNjAwMDgxbWYyMQ==" target="_blank" style="color: #00e5ff;">Instagram</a> for updates.</p></div>
    </div>

    <button onclick="closeFlashcardPopup()" class="option" style="background-color: #3498db; color: white; margin-top: 10px;">Close</button>
</div>
<script>
    function openFlashcardPopup() {
        document.getElementById('flashcardPopup').style.display = 'block';
    }

    function closeFlashcardPopup() {
        document.getElementById('flashcardPopup').style.display = 'none';
    }

    function flipCard(card) {
        var front = card.querySelector(".card-front");
        var back = card.querySelector(".card-back");
        
        if (back.style.display === "none") {
            front.style.display = "none";
            back.style.display = "block";
        } else {
            front.style.display = "block";
            back.style.display = "none";
        }
    }

    function showPage(page) {
        document.getElementById(`${currentPage}Container`).classList.add('hidden');
        document.getElementById(`${page}Container`).classList.remove('hidden');
        document.getElementById('backButton').style.display = (page !== 'login') ? 'block' : 'none';

        // Show elements only on login view
        if (page === 'login') {
            document.getElementById('aboutUsContainer').classList.remove('hidden');
            document.getElementById('announcementContainer').classList.remove('hidden');
            document.getElementById('flashcardButton').style.display = 'block'; 
            document.getElementById('flashcardPopup').style.display = 'none';  
        } else {
            document.getElementById('aboutUsContainer').classList.add('hidden');
            document.getElementById('announcementContainer').classList.add('hidden');
            document.getElementById('flashcardButton').style.display = 'none';  
            document.getElementById('flashcardPopup').style.display = 'none';  
        }

        currentPage = page;
    }
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

            var responses = {
                "notes": "You can find notes in the study material section of your class.",
                "timetable": "The timetable is available under the 'Timetable' TG group, try asking in TG chat group.",
                "ast": "AST (AcademeForge Scholars Test) is an exam for students from Class 1 to 10. Visit the WordPress website for details!",
                "extra study material": "Extra study materials are available in the 'Extra Material' website.",
                "about us": "AcademeForge is an educational platform founded by Devraj Kumar and co-founded by Aadi & Mandeep.",
                "hello": "Hello! How can I assist you today?",
                "hi": "Hi there! Need help?",
                "bye": "Goodbye! Happy studying!"
            };

            var response = responses[input] || "I'm a small chatbox created by AcademeForge. I can only answer specific questions. Try asking about: Notes, Timetable, AST, Extra Study Material, or About Us";
            chatbox.innerHTML += "<p><strong>You:</strong> " + input + "</p>";
            chatbox.innerHTML += "<p><strong>Bot:</strong> " + response + "</p>";

            document.getElementById('chatbotInput').value = "";
            chatbox.scrollTop = chatbox.scrollHeight;
        }
    }

</script>

</body>
</html>








<div class="container" id="loginContainer">
  <marquee behavior="scroll" direction="left">
    Welcome to AcademeForge – Something Out Of The Box!
  </marquee>
  <h2>LOGIN</h2>
  <input type="email" id="email" placeholder="Enter your Gmail" class="animate-input" />
  <button onclick="sendOtp()">Send OTP</button>
  <div id="otpSection" style="display:none;">
    <input type="text" id="otp" placeholder="Enter OTP" class="animate-input" />
    <button onclick="verifyOtp()">Verify OTP</button>
  </div>
  <p id="error"></p>
</div>

<!-- Firebase SDKs -->
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-app.js"></script>
<script src="https://www.gstatic.com/firebasejs/9.6.1/firebase-auth.js"></script>

<script>
  // Firebase configuration (replace with your own Firebase project's details)
  const firebaseConfig = {
    apiKey: "YOUR_API_KEY",
    authDomain: "YOUR_AUTH_DOMAIN",
    projectId: "YOUR_PROJECT_ID",
    storageBucket: "YOUR_STORAGE_BUCKET",
    messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
    appId: "YOUR_APP_ID"
  };

  // Initialize Firebase
  const app = firebase.initializeApp(firebaseConfig);
  const auth = firebase.auth();

  function sendOtp() {
    const email = document.getElementById("email").value;
    const error = document.getElementById("error");

    if (!email) {
      error.style.display = 'block';
      error.innerText = "Please enter your Gmail!";
      return;
    }

    // Create a phone number (for testing purposes, use a number linked with your Firebase)
    const phoneNumber = "+1234567890"; // Dummy number for Firebase testing

    // Send OTP
    const appVerifier = new firebase.auth.RecaptchaVerifier('sendOtp', {
      size: 'invisible',
      callback: function(response) {
        // reCAPTCHA solved - can proceed with OTP sending
      }
    });

    auth.signInWithPhoneNumber(phoneNumber, appVerifier)
      .then((confirmationResult) => {
        window.confirmationResult = confirmationResult;
        document.getElementById("otpSection").style.display = "block";
        error.style.display = 'none';
      })
      .catch((error) => {
        error.style.display = 'block';
        error.innerText = "Error sending OTP. Please try again!";
      });
  }

  function verifyOtp() {
    const otp = document.getElementById("otp").value;
    const error = document.getElementById("error");

    if (!otp) {
      error.style.display = 'block';
      error.innerText = "Please enter OTP!";
      return;
    }

    window.confirmationResult.confirm(otp)
      .then((result) => {
        const user = result.user;
        alert("Login Successful!");
        // Redirect or load the user dashboard
      })
      .catch((error) => {
        error.style.display = 'block';
        error.innerText = "Invalid OTP. Please try again!";
      });
  }
</script>


