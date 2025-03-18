<html lang="en">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <title>AcademeForge</title>  
    <style>  
        body {  
            font-family: Arial, sans-serif;  
            background-color: #f4f4f4;  
            text-align: center;  
            padding: 20px;  
        }  
        #container {  
            max-width: 500px;  
            margin: auto;  
            background: white;  
            padding: 20px;  
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);  
            border-radius: 10px;  
        }  
        input, button, select {  
            width: 100%;  
            padding: 10px;  
            margin: 10px 0;  
            border-radius: 5px;  
            border: 1px solid #ddd;  
        }  
        button {  
            background-color: #007BFF;  
            color: white;  
            cursor: pointer;  
        }  
        button:hover {  
            background-color: #0056b3;  
        }  
        #subjectList img {  
            width: 50px;  
            height: 50px;  
            margin-right: 10px;  
        }  
        .hidden {  
            display: none;  
        }  
    </style>  
</head>  
<body>  <div id="container">  
    <h2>Login</h2>  
    <input type="text" id="username" placeholder="Username">  
    <input type="password" id="password" placeholder="Password">  
    <button onclick="login()">Sign In</button>  
</div>  

<div id="classSelection" class="hidden">  
    <h2>Select Your Class</h2>  
    <select id="classSelect" onchange="selectClass()">  
        <option value="">--Select Class--</option>  
        <option value="9">Class 9</option>  
        <option value="10">Class 10</option>  
        <option value="11">Class 11</option>  
        <option value="12">Class 12</option>  
    </select>  
</div>  

<div id="streamSelection" class="hidden">  
    <h2>Select Your Stream</h2>  
    <select id="streamSelect" onchange="selectStream()">  
        <option value="">--Select Stream--</option>  
        <option value="Science">Science</option>  
        <option value="Commerce">Commerce</option>  
        <option value="Arts">Arts</option>  
    </select>  
</div>  

<div id="subjectContainer" class="hidden">  
    <h2>Subjects</h2>  
    <ul id="subjectList"></ul>  
    <button onclick="goBack()">Back</button>  
</div>  

<div id="extraSections" class="hidden">  
    <h2>Extra Study Materials</h2>  
    <p>Coming soon...</p>  
    <h2>Timetable</h2>

<html lang="en">  
<head>  
    <meta charset="UTF-8" />  
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
    <title>Study Timetable</title>  
    <style>  
        body {  
            font-family: Arial, sans-serif;  
            margin: 20px;  
        }  
        .hidden {  
            display: none;  
        }  
        button {  
            padding: 10px 20px;  
            background-color: #4CAF50;  
            color: white;  
            border: none;  
            cursor: pointer;  
            border-radius: 5px;  
            margin: 10px;  
            transition: background-color 0.3s;  
        }  
        button:hover {  
            background-color: #45a049;  
        }  
        table {  
            width: 100%;  
            border-collapse: collapse;  
            margin-top: 20px;  
        }  
        th, td {  
            padding: 10px;  
            border: 1px solid #ccc;  
            text-align: center;  
        }  
        th {  
            background-color: #f2f2f2;  
        }  
    </style>  
</head>  
<body>  
<!-- Class Selection Section -->  
<div id="classSelectionSection">  
    <h1>Select Your Class</h1>  
    <button onclick="selectClass(9)">Class 9</button>  
    <button onclick="selectClass(10)">Class 10</button>  
    <button onclick="selectClass(11)">Class 11</button>  
    <button onclick="selectClass(12)">Class 12</button>  
</div>  <!-- Main Options (Visible All the Time) -->  <div id="mainOptionsSection">  
    <button onclick="showTimetable()">Timetable</button>  
    <button onclick="showNotes()">Access Notes</button>  
    <button onclick="showExtraMaterials()">Extra Study Materials</button>  
</div>  <!-- Timetable Section (Hidden by Default) -->  <div id="mainTimetableSection" style="display: none;">  
    <h1>Select Your Timetable</h1>  
    <button onclick="showTimetableDetails('regular')">Regular</button>  
    <button onclick="showTimetableDetails('dummy')">Dummy</button>  
</div>  <!-- Regular Timetable Section -->  <div id="regularTimetableSection" style="display: none;">  
    <h2>Regular Student Timetable</h2>  
    <table>  
        <tr><th>Time</th><th>Activity</th></tr>  
        <tr><td>8:00 AM - 2:00 PM</td><td>School Time</td></tr>  
        <tr><td>2:30 PM - 3:30 PM</td><td>Lunch + Rest</td></tr>  
        <tr><td>3:30 PM - 5:30 PM</td><td>Self Study (Math/Physics/Chemistry)</td></tr>  
        <tr><td>5:30 PM - 6:30 PM</td><td>Break/Exercise</td></tr>  
        <tr><td>6:30 PM - 8:30 PM</td><td>Self Study (Biology/English/Hindi)</td></tr>  
        <tr><td>8:30 PM - 9:30 PM</td><td>Dinner + Family Time</td></tr>  
        <tr><td>9:30 PM - 10:30 PM</td><td>Revision + Planning for Next Day</td></tr>  
    </table>  
    <button onclick="backToTimetable()">Back</button>  
</div>  <!-- Dummy Timetable Section -->  <div id="dummyTimetableSection" style="display: none;">  
    <h2>Dummy Student Timetable</h2>  
    <table>  
        <tr><th>Time</th><th>Activity</th></tr>  
        <tr><td>8:00 AM - 9:00 AM</td><td>Exercise + Freshen Up</td></tr>  
        <tr><td>9:00 AM - 10:30 AM</td><td>Math/Physics Study</td></tr>  
        <tr><td>10:30 AM - 11:00 AM</td><td>Short Break</td></tr>  
        <tr><td>11:00 AM - 12:30 PM</td><td>Chemistry/Biology Study</td></tr>  
        <tr><td>12:30 PM - 1:30 PM</td><td>Lunch + Rest</td></tr>  
        <tr><td>1:30 PM - 3:00 PM</td><td>English/Hindi Study</td></tr>  
        <tr><td>3:00 PM - 4:00 PM</td><td>Short Break + Refresh</td></tr>  
        <tr><td>4:00 PM - 6:00 PM</td><td>Revision + Problem Solving</td></tr>  
        <tr><td>6:00 PM - 7:00 PM</td><td>Break/Exercise</td></tr>  
        <tr><td>7:00 PM - 9:00 PM</td><td>Subject-Wise Study + Homework</td></tr>  
        <tr><td>9:00 PM - 10:00 PM</td><td>Dinner + Relax</td></tr>  
        <tr><td>10:00 PM - 11:00 PM</td><td>Light Reading + Planning</td></tr>  
    </table>  
    <button onclick="backToTimetable()">Back</button>  
</div>  <!-- JavaScript -->  <script>  
    // Hides only class buttons after selection (keeps other buttons visible)  
    function selectClass(classNumber) {  
        const classButtons = document.querySelectorAll('#classSelectionSection button');  
        classButtons.forEach(button => button.style.display = 'none');  
    }  
  
    // Displays timetable selection  
    function showTimetable() {  
        document.getElementById('mainTimetableSection').style.display = 'block';  
        document.getElementById('regularTimetableSection').style.display = 'none';  
        document.getElementById('dummyTimetableSection').style.display = 'none';  
    }  
  
    // Displays timetable details  
    function showTimetableDetails(type) {  
        document.getElementById('mainTimetableSection').style.display = 'none';  
        if (type === 'regular') {  
            document.getElementById('regularTimetableSection').style.display = 'block';  
        } else {  
            document.getElementById('dummyTimetableSection').style.display = 'block';  
        }  
    }  
  
    // Back button for timetable  
    function backToTimetable() {  
        document.getElementById('mainTimetableSection').style.display = 'block';  
        document.getElementById('regularTimetableSection').style.display = 'none';  
        document.getElementById('dummyTimetableSection').style.display = 'none';  
    }  
</script>  <div id="reviewsSection" class="hidden">  
    <h2>Student Reviews</h2>  
    <p>"This website helped me so much in my studies!" - Newton</p>  
    <p>"AcademeForge is amazing for study materials!" - Einstein</p>

lang="en">

<head>  
    <meta charset="UTF-8" />  
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />  
    <title>AcademeForge</title>  
    <style>  
        body {  
            font-family: Arial, sans-serif;  
            margin: 20px;  
        }  
        .hidden {  
            display: none;  
        }  
        #aboutUsSection {  
            transition: opacity 0.3s ease;  
            padding: 20px;  
            border: 1px solid #ccc;  
            border-radius: 5px;  
            background-color: #f9f9f9;  
            margin-top: 10px;  
        }  
        button {  
            padding: 10px 20px;  
            background-color: #4CAF50;  
            color: white;  
            border: none;  
            cursor: pointer;  
            border-radius: 5px;  
            margin-top: 10px;  
            transition: background-color 0.3s;  
        }  
        button:hover {  
            background-color: #45a049;  
        }  
    </style>  
</head>  
<body>  <!-- About Us Button -->  
<button onclick="showAboutUs()">About Us</button>

<!-- About Us Section (Hidden Initially) -->  <div id="aboutUsSection" class="hidden">  
    <h2>About Us</h2>  
    <p>AcademeForge was founded by <b>Devraj Kumar</b> and co-founded by <b>Aadi</b> and <b>Mandeep</b>. Our mission is to provide free study materials to students and help them achieve academic success.</p>  
    <button onclick="hideAboutUs()">Back</button>  
</div>  <!-- JavaScript (Directly in HTML) -->  <script>  
    function showAboutUs() {  
        document.getElementById('aboutUsSection').style.display = 'block';  
        document.getElementById('mainSection').style.display = 'none';  
    }  
  
    function hideAboutUs() {  
        document.getElementById('aboutUsSection').style.display = 'none';  
        document.getElementById('mainSection').style.display = 'block';  
    }  
</script>  </body>  
</html>  <script>  
    function login() {  
        document.getElementById('container').style.display = 'none';  
        document.getElementById('classSelection').classList.remove('hidden');  
    }  
  
    function selectClass() {  
        const selectedClass = document.getElementById('classSelect').value;  
  
        if (selectedClass === '11' || selectedClass === '12') {  
            document.getElementById('classSelection').classList.add('hidden');  
            document.getElementById('streamSelection').classList.remove('hidden');  
        } else if (selectedClass === '9' || selectedClass === '10') {  
            displaySubjects(selectedClass, null);  
        }  
    }  
  
    function selectStream() {  
        const selectedClass = document.getElementById('classSelect').value;  
        const selectedStream = document.getElementById('streamSelect').value;  
        displaySubjects(selectedClass, selectedStream);  
    }  
  
    function displaySubjects(selectedClass, selectedStream) {  
        const subjects = {  
            '9': ['Mathematics', 'Science', 'Social Science', 'English', 'Hindi'],  
            '10': ['Mathematics', 'Science', 'Social Science', 'English', 'Hindi'],  
            '11-Science': ['Physics', 'Chemistry', 'Biology', 'Mathematics', 'English'],  
            '11-Commerce': ['Accountancy', 'Business Studies', 'Economics', 'Mathematics', 'English'],  
            '11-Arts': ['History', 'Geography', 'Political Science', 'Sociology', 'English'],  
            '12-Science': ['Physics', 'Chemistry', 'Biology', 'Mathematics', 'English'],  
            '12-Commerce': ['Accountancy', 'Business Studies', 'Economics', 'Mathematics', 'English'],  
            '12-Arts': ['History', 'Geography', 'Political Science', 'Sociology', 'English']  
        };  
  
        const key = selectedStream ? `${selectedClass}-${selectedStream}` : selectedClass;  
        const subjectList = subjects[key] || [];  
        const listContainer = document.getElementById('subjectList');  
  
        listContainer.innerHTML = '';  
        subjectList.forEach(subject => {  
            listContainer.innerHTML += `<li><img src="https://via.placeholder.com/50" alt="subject"> ${subject} <button onclick="alert('Google link coming soon')">Access to Notes</button></li>`;  
        });  
  
        document.getElementById('streamSelection').classList.add('hidden');  
        document.getElementById('classSelection').classList.add('hidden');  
        document.getElementById('subjectContainer').classList.remove('hidden');  
        document.getElementById('extraSections').classList.remove('hidden');  
        document.getElementById('reviewsSection').classList.remove('hidden');  
        document.getElementById('founderSection').classList.remove('hidden');  
    }  
  
    function goBack() {  
        document.getElementById('subjectContainer').classList.add('hidden');  
        document.getElementById('classSelection').classList.remove('hidden');  
    }  
</script>  </body>  
</html>  Fix this correctly remove all the bugs

