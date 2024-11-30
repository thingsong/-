<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>퀴즈 시스템</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f5f5f5;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 400px;
            margin: 100px auto;
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            text-align: center;
        }
        .button {
            display: block;
            width: 100%;
            padding: 15px;
            margin: 10px 0;
            border: none;
            border-radius: 4px;
            font-size: 16px;
            cursor: pointer;
            color: white;
            transition: background-color 0.2s;
        }
        .teacher-btn {
            background-color: #007bff;
        }
        .teacher-btn:hover {
            background-color: #0056b3;
        }
        .student-btn {
            background-color: #28a745;
        }
        .student-btn:hover {
            background-color: #218838;
        }
        input {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 16px;
            box-sizing: border-box;
        }
        .login-form {
            display: none;
            margin-top: 20px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 4px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>퀴즈 시스템</h1>
        
        <button onclick="showTeacherLogin()" class="button teacher-btn">교사 모드</button>
        <button onclick="showStudentLogin()" class="button student-btn">학생 모드</button>

        <!-- 교사 로그인 폼 -->
        <div id="teacherLogin" class="login-form">
            <input type="password" id="teacherPassword" placeholder="교사 비밀번호">
            <button onclick="loginTeacher()" class="button teacher-btn">로그인</button>
        </div>

        <!-- 학생 로그인 폼 -->
        <div id="studentLogin" class="login-form">
            <input type="text" id="studentName" placeholder="이름을 입력하세요">
            <button onclick="loginStudent()" class="button student-btn">시작하기</button>
        </div>
    </div>

    <script>
        const TEACHER_PASSWORD = "1234"; // 교사 비밀번호

        function showTeacherLogin() {
            document.getElementById('teacherLogin').style.display = 'block';
            document.getElementById('studentLogin').style.display = 'none';
        }

        function showStudentLogin() {
            document.getElementById('studentLogin').style.display = 'block';
            document.getElementById('teacherLogin').style.display = 'none';
        }

        function loginTeacher() {
            const password = document.getElementById('teacherPassword').value;
            if (password === TEACHER_PASSWORD) {
                window.location.href = 'teacher.html';
            } else {
                alert('비밀번호가 틀렸습니다.');
            }
        }

        function loginStudent() {
            const name = document.getElementById('studentName').value.trim();
            if (name) {
                localStorage.setItem('studentName', name);
                window.location.href = 'student.html';
            } else {
                alert('이름을 입력해주세요.');
            }
        }
    </script>
</body>
</html>
