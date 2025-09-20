<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>BrainCraft Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f3ff;
      color: #333;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .quiz-container {
      background: #fff;
      padding: 20px;
      border-radius: 15px;
      width: 400px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      text-align: center;
    }
    h1 {
      margin-bottom: 20px;
      color: #6a0dad;
    }
    .question {
      font-size: 18px;
      margin-bottom: 15px;
    }
    .options button {
      display: block;
      width: 100%;
      margin: 8px 0;
      padding: 10px;
      border: none;
      border-radius: 8px;
      background: #eee;
      cursor: pointer;
      transition: 0.3s;
    }
    .options button:hover {
      background: #dcd0ff;
    }
    #next-btn {
      margin-top: 20px;
      background: #6a0dad;
      color: white;
      padding: 10px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      display: none;
    }
  </style>
</head>
<body>
  <div class="quiz-container">
    <h1>BrainCraft Quiz 🧠</h1>
    <div id="quiz">
      <div class="question" id="question">Loading...</div>
      <div class="options" id="options"></div>
      <button id="next-btn">Next</button>
    </div>
  </div>

  <script>
    const questions = [
      {
        question: "Which planet is known as the Red Planet?",
        options: ["Earth", "Mars", "Jupiter", "Venus"],
        answer: 1
      },
      {
        question: "Who developed the theory of relativity?",
        options: ["Isaac Newton", "Albert Einstein", "Tesla", "Galileo"],
        answer: 1
      },
      {
        question: "What is the capital of Nigeria?",
        options: ["Lagos", "Abuja", "Port Harcourt", "Kano"],
        answer: 1
      }
    ];

    let currentQuestion = 0;
    let score = 0;

    const questionEl = document.getElementById("question");
    const optionsEl = document.getElementById("options");
    const nextBtn = document.getElementById("next-btn");

    function loadQuestion() {
      let q = questions[currentQuestion];
      questionEl.textContent = q.question;
      optionsEl.innerHTML = "";
      q.options.forEach((opt, i) => {
        let btn = document.createElement("button");
        btn.textContent = opt;
        btn.onclick = () => selectAnswer(i);
        optionsEl.appendChild(btn);
      });
    }

    function selectAnswer(i) {
      if (i === questions[currentQuestion].answer) {
        score++;
      }
      nextBtn.style.display = "block";
    }

    nextBtn.addEventListener("click", () => {
      currentQuestion++;
      if (currentQuestion < questions.length) {
        loadQuestion();
        nextBtn.style.display = "none";
      } else {
        showResult();
      }
    });

    function showResult() {
      questionEl.textContent = `Quiz Over! 🎉 Your score: ${score}/${questions.length}`;
      optionsEl.innerHTML = "";
      nextBtn.style.display = "none";
    }

    loadQuestion();
  </script>
</body>
</html>
