html lang="en">
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
            display: none;
        }
        h2 {
            margin-top: 0;
        }
        input, button, select {
            width: calc(100% - 20px);
            padding: 10px;
            margin: 10px 0;
            border-radius: 5px;
            border: 1px solid #ddd;
            box-sizing: border-box;
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
        #subjectList img {
            width: 40px;
            height: 40px;
            margin-right: 10px;
            vertical-align: middle;
        }
        ul {
            list-style-type: none;
            padding: 0;
        }
        li {
            display: flex;
            align-items: center;
            margin: 10px 0;
        }
        .hidden {
            display: none;
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
<div id="classSelection">
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
<div id="streamSelection">
    <h2>Select Your Stream</h2>
    <select id="streamSelect" onchange="selectStream()">
        <option value="">--Select Stream--</option>
        <option value="Science">Science</option>
        <option value="Commerce">Commerce</option>
        <option value="Arts">Arts</option>
    </select>
</div>

<!-- Subject List Section -->
<div id="subjectContainer">
    <h2>Subjects</h2>
    <ul id="subjectList"></ul>
    <button onclick="goBack()">Back</button>
</div>

<!-- Extra Study Materials Section -->
<div id="extraSections">
    <h2>Extra Study Materials</h2>
    <p>Coming soon...</p>
    <h2>Timetable</h2>
    <p>Timetable feature coming soon...</p>
</div>

<!-- Reviews Section -->
<div id="reviewsSection">
    <h2>Student Reviews</h2>
    <p>"This website helped me so much in my studies!" - Newton</p>
    <p>"AcademeForge is amazing for study materials!" - Einstein</p>
</div>

<!-- About Us Section -->
<div id="aboutUsSection">
    <h2>About Us</h2>
    <p>AcademeForge was founded by <b>Devraj Kumar</b> and co-founded by <b>Aadi</b> and <b>Mandeep</b>. Our mission is to provide free study materials to students and help them achieve academic success.</p>
    <button onclick="hideAboutUs()">Back</button>
</div>

<button onclick="showAboutUs()">About Us</button>

<!-- JavaScript -->
<script>
    function login() {
        document.getElementById('container').style.display = 'none';
        document.getElementById('classSelection').style.display = 'block';
    }

    function selectClass() {
        const selectedClass = document.getElementById('classSelect').value;

        if (selectedClass === '11' || selectedClass === '12') {
            document.getElementById('classSelection').style.display = 'none';
            document.getElementById('streamSelection').style.display = 'block';
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
            listContainer.innerHTML += `<li><img src="https://via.placeholder.com/40" alt="subject"> ${subject} <button onclick="alert('Google link coming soon')">Access to Notes</button></li>`;
        });

        document.getElementById('streamSelection').style.display = 'none';
        document.getElementById('subjectContainer').style.display = 'block';
        document.getElementById('extraSections').style.display = 'block';
        document.getElementById('reviewsSection').style.display = 'block';
    }

    function goBack() {
        document.getElementById('subjectContainer').style.display = 'none';
        document.getElementById('classSelection').style.display = 'block';
    }

    function showAboutUs() {
        document.getElementById('aboutUsSection').style.display = 'block';
    }

    function hideAboutUs() {
        document.getElementById('aboutUsSection').style.display = 'none';
    }
</script>

</body>
</html>
