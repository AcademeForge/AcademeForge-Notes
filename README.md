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
        #container, #classSelection, #streamSelection, #subjectContainer, #extraSections, #reviewsSection, #aboutUsSection {  
            max-width: 500px;  
            margin: auto;  
            background: white;  
            padding: 20px;  
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);  
            border-radius: 10px;  
            margin-bottom: 20px;  
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
            border: none;  
            transition: background-color 0.3s;  
        }  
        button:hover {  
            background-color: #0056b3;  
        }  
        .hidden {  
            display: none;  
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

<!-- Login Section -->
<div id="container">  
    <h2>Login</h2>  
    <input type="text" id="username" placeholder="Username">  
    <input type="password" id="password" placeholder="Password">  
    <button onclick="login()">Sign In</button>  
</div>  

<!-- Class Selection Section -->
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

<!-- Stream Selection Section -->
<div id="streamSelection" class="hidden">  
    <h2>Select Your Stream</h2>  
    <select id="streamSelect" onchange="selectStream()">  
        <option value="">--Select Stream--</option>  
        <option value="Science">Science</option>  
        <option value="Commerce">Commerce</option>  
        <option value="Arts">Arts</option>  
    </select>  
</div>  

<!-- Subjects Section -->
<div id="subjectContainer" class="hidden">  
    <h2>Subjects</h2>  
    <ul id="subjectList"></ul>  
    <button onclick="goBack()">Back</button>  
</div>  

<!-- Extra Study Materials Section -->
<div id="extraSections" class="hidden">  
    <h2>Extra Study Materials</h2>  
    <p>Coming soon...</p>  
</div>  

<!-- Timetable Section -->
<div id="mainTimetableSection" class="hidden">  
    <h1>Select Your Timetable</h1>  
    <button onclick="showTimetableDetails('regular')">Regular</button>  
    <button onclick="showTimetableDetails('dummy')">Dummy</button>  
</div>  

<!-- Regular Timetable -->
<div id="regularTimetableSection" class="hidden">  
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
</div>  

<!-- Dummy Timetable -->
<div id="dummyTimetableSection" class="hidden">  
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
</div>  

<!-- JavaScript -->
<script>
    function login() {
        document.getElementById('container').style.display = 'none';
        document.getElementById('classSelection').classList.remove('hidden');
    }

    function goBack() {
        document.getElementById('subjectContainer').classList.add('hidden');
        document.getElementById('classSelection').classList.remove('hidden');
    }
</script>  

</body>  
</html>