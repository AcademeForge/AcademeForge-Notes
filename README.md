<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AcademeForge</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f9;
            color: #333;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow-y: auto;
            animation: fadeIn 0.5s ease-in-out;
        }
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
        .container {
            width: 90%;
            max-width: 400px;
            padding: 20px;
            background-color: #ffffff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            text-align: center;
            animation: slideIn 0.5s ease-in-out;
        }
        @keyframes slideIn {
            from { transform: translateY(-20px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }
        h2 {
            color: #4CAF50;
            font-size: 24px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px;
            margin-top: 10px;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease;
            width: 100%;
            font-size: 16px;
        }
        button:hover {
            background-color: #45a049;
            transform: scale(1.05);
        }
        .hidden {
            display: none;
            animation: fadeIn 0.3s ease;
        }
        .extra-materials {
            margin-top: 20px;
            text-align: center;
        }
        .extra-materials a {
            display: inline-block;
            background-color: #2196F3;
            color: white;
            padding: 12px;
            border-radius: 5px;
            text-decoration: none;
            font-size: 16px;
            transition: background-color 0.3s ease, transform 0.2s ease;
        }
        .extra-materials a:hover {
            background-color: #1976D2;
            transform: scale(1.05);
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Welcome to AcademeForge</h2>
    <button onclick="showClasses()">Access Study Materials</button>
    <div id="class-selection" class="hidden">
        <button onclick="showStreams('11')">Class 11</button>
        <button onclick="showStreams('12')">Class 12</button>
    </div>

    <div id="stream-selection" class="hidden">
        <button onclick="showSubjects('Science')">Science</button>
        <button onclick="showSubjects('Commerce')">Commerce</button>
        <button onclick="showSubjects('Arts')">Arts</button>
    </div>

    <div id="subject-selection" class="hidden">
        <button>Physics</button>
        <button>Chemistry</button>
        <button>Math</button>
        <button>Biology</button>
        <button>English</button>
        <button>Hindi</button>
    </div>

    <div class="extra-materials">
        <a href="https://academeforge.pages.dev/" target="_blank">Extra Study Materials</a>
    </div>
</div>

<script>
    function showClasses() {
        document.getElementById('class-selection').classList.remove('hidden');
    }

    function showStreams(classNum) {
        document.getElementById('stream-selection').classList.remove('hidden');
    }

    function showSubjects(stream) {
        document.getElementById('subject-selection').classList.remove('hidden');
    }
</script>

</body>
</html>