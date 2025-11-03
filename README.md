# 2.1.3-Career-Preparation
Answer the 20 yes or no questions. The results will state which career pathway best aligns with your interests. Then go back to Edio to share your results!

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Career Interest Survey</title>
  <style>
    body {
      background-color: white;
      font-family: Arial, sans-serif;
      color: #003366;
      text-align: center;
      padding: 20px;
    }
    .question-box {
      border: 2px solid #003366;
      padding: 20px;
      margin: 20px auto;
     : #f0f8ff;
    }
    .question-image {
      max-width: 100%;
      height: auto;
    }
    button {
      background-color: #ffcc00;
      color: #003366;
      border: none;
      padding: 10px 20px;
      margin: 10px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }
    #result {
      font-size: 24px;
      font-weight: bold;
      margin-top: 20px;
    }
  </style>
</head>
<body>
 img id="question-image" class="question-image" src="" alt="Question Image" />
    <p id="question-text"></p>
    <button onclick="answer('yes')">Yes</button>
    <button onclick="answer('no')">No</button>
  </div>
  <div id="result"></div>
  <button onclick="retakeSurvey()" style="display:none;">Retake Survey</button>

  <script>
    const questions = [
      { text: "Do you enjoy expressing yourself through writing, music, or visual arts?", category: "Arts & Communication", image: "https://cdn.pixabay.com/photo/2019/02/04/14/59/artist-3972061_1280.jpg" },
      { text: "Do you like creating videos, graphics, or digital content?", category: "Arts & Communication", image: "https://cdn.pixabay.com/photo/2018/10/29/21/46/tv-3782178_1280.jpg" },
      { text: "Do you enjoy performing or speaking in front of others?", category: "Arts & Communication", image: "https://cdn.pixabay.com/photo/2020/06/14/17/53/music-5298376_1280.jpg" },
      { text: "Do you often come up with creative ideas or solutions?", category: "Arts & Communication", image: "https://cdn.pixabay.com/photo/2023/04/06/10/56/artist-7902727_1280.jpg" },
      { text: "Do you enjoy helping others solve problems or feel better?", category: "Human Services", image: "https://cdn.pixabay.com/photo/2023/06/26/17/10/elderly-8091600_1280.jpg" },
      { text: "Do you like working with children, the elderly, or people in need?", category: "Human Services", image: "https://cdn.pixabay.com/photo/2019/10/23/18/23/preschool-4573176_1280.jpg" },
      { text: "Do you feel fulfilled when you make a positive difference in someone’s life?", category: "Human Services", image: "https://cdn.pixabay.com/photo/2017/07/31/11/21/female-2558594_1280.jpg" },
      { text: "Do you enjoy listening and giving advice to others?", category: "Human Services", image: "https://cdn.pixabay.com/photo/2023/11/01/10/56/ai-generated-8356227_1280.jpg" },
      { text: "Do you enjoy organizing tasks, data, or schedules?", category: "Business Information Technology", image: "https://cdn.pixabay.com/photo/2023/09/26/10/35/finance-8277276_1280.jpg" },
      { text: "Are you interested in how businesses operate or how money is managed?", category: "Business Information Technology", image: "https://cdn.pixabay.com/photo/2020/05/29/08/29/job-5234968_1280.jpg" },
      { text: "Do you like working with computers or learning new software?", category: "Business Information Technology", image: "https://cdn.pixabay.com/photo/2016/11/19/14/00/coding-1839406_1280.jpg" },
      { text: "Do you enjoy solving problems using logic and analysis?", category: "Business Information Technology", image: "https://cdn.pixabay.com/photo/2017/03/23/12/36/startup-2161812_1280.jpg" },
      { text: "Do you enjoy working with your hands or building things?", category: "Industrial Technology", image: "https://cdn.pixabay.com/photo/2016/11/29/04/17/woodworking-1867380_1280.jpg" },
      { text: "Are you interested in how machines or tools work?", category: "Industrial Technology", image: "https://cdn.pixabay.com/photo/2015/03/26/09/54/excavator-690903_1280.jpg" },
      { text: "Do you like fixing or improving physical objects?", category: "Industrial Technology", image: "https://cdn.pixabay.com/photo/2015/07/17/22/43/auto-repair-849849_1280.jpg" },
      { text: "Do you enjoy learning through hands-on activities?", category: "Industrial Technology", image: "https://cdn.pixabay.com/photo/2016/11/29/09/32/tools-1867296_1280.jpg" },
      { text: "Are you curious about how the human body or nature works?", category: "Science/Health", image: "https://cdn.pixabay.com/photo/2021/01/26/14/41/anatomy-5951556_1280.jpg" },
      { text: "Do you enjoy conducting experiments or solving scientific problems?", category: "Science/Health", image: "https://cdn.pixabay.com/photo/2016/11/29/03/53/microscope-1862616_1280.jpg" },
      { text: "Are you interested in medicine, health, or helping people stay well?", category: "Science/Health", image: "https://cdn.pixabay.com/photo/2016/10/18/21/22/nurse-1759180_1280.jpg" },
      { text: "Do you like learning about biology, chemistry, or physics?", category: "Science/Health", image: "https://cdn.pixabay.com/photo/2014/04/03/10/32/laboratory-311871_1280.png" }
    ];

    let currentQuestion = 0;
    const scores = {
      "Arts & Communication": 0,
      "Human Services": 0,
      "Business Information Technology": 0,
      "Industrial Technology": 0,
      "Science/Health": 0
    };

    function showQuestion() {
      const q = questions[currentQuestion];
      document.getElementById("question-text").innerText = q.text;
      document.getElementById("question-image").src = q.image;
    }

    function answer(response) {
      if (response === 'yes') {
        scores[questions[currentQuestion].category]++;
      }
      currentQuestion++;
      if (currentQuestion < questions.length) {
        showQuestion();
      } else {
        showResult();
      }
    }

    function showResult() {
      document.getElementById("survey-container").style.display = 'none';
      const topCategory = Object.keys(scores).reduce((a, b) => scores[a] > scores[b] ? a : b);
      document.getElementById("result").innerText = `Congrats! Your career pathway match is ${topCategory}`;
      document.querySelector("button[onclick='retakeSurvey()']").style.display = 'inline-block';
    }

    function retakeSurvey() {
      currentQuestion = 0;
      for (let key in scores) scores[key] = 0;
      document.getElementById("survey-container").style.display = 'block';
      document.getElementById("result").innerText = '';
      document.querySelector("button[onclick='retakeSurvey()']").style.display = 'none';
      showQuestion();
    }

    showQuestion();
  </script>
</body>
</html>
