<style>
  #start-screen {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: #d0e9cd;
    font-family: Arial, sans-serif;
    font-weight: bold;
    text-align: center;
  }

  #start-screen h1 {
    font-size: 2em;
    margin-bottom: 1em;
  }

  #start-button {
    background-color: #4b8b60;
    color: white;
    font-size: 1.2em;
    padding: 10px 20px;
    border: none;
    border-radius: 12px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }

  #start-button:hover {
    background-color: #3a6e4c;
  }

  #quiz-container {
    display: none;
  }
</style>

<div id="start-screen">
  <h1>Kamu mirip OC-nya mumut yang mana yaah?</h1>
  <button id="start-button">Start</button>
</div>

<script>
  document.addEventListener("DOMContentLoaded", function() {
    document.getElementById("start-button").addEventListener("click", function() {
      document.getElementById("start-screen").style.display = "none";
      document.getElementById("quiz-container").style.display = "block";
    });
  });
</script>
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Love Quiz - Mumut's OCs</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #d9f2d9;
      padding: 20px;
      text-align: center;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
      background: white;
      border-radius: 10px;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h1 {
      font-size: 24px;
      margin-bottom: 20px;
    }
    .question-box {
      background-color: #97cfa1;
      border-radius: 8px;
      padding: 15px;
      margin-bottom: 20px;
    }
    .answer {
      display: block;
      background-color: #ffffff;
      border: 2px solid #5c9b66;
      color: #333;
      font-weight: bold;
      padding: 10px;
      margin: 10px 0;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .answer:hover {
      background-color: #e0f2e0;
    }
    #start-screen, #quiz-screen, #result-screen {
      display: none;
    }
    button {
      background-color: #5c9b66;
      color: white;
      font-weight: bold;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #4a8052;
    }
  </style>
</head>
<body>
  <div class="container">
    <div id="start-screen">
      <h1>Kamu mirip OC-nya mumut yang siapa yach?</h1>
      <button onclick="startQuiz()">Start</button>
    </div><div id="quiz-screen">
  <div id="quiz-box"></div>
</div>

<div id="result-screen">
  <h1>Hasil kamu adalah:</h1>
  <p id="result-text"></p>
</div>

  </div>  <script>
    const quizData = [
      {
        question: "Kamu kalau punya crush biasanya ngapain?",
        answers: [
          { text: "Biasa aja, memilih jalur langit yaitu doain dia aja", character: "Alex" },
          { text: "Langsung pamer ke temen, ajakin dia kenalan, bahkan godain dia!", character: "Xen" },
          { text: "Ngasih dia jajan, hadiah kecil, atau oleh-oleh, berharap dia notice kamu", character: "Eric" },
          { text: "Pengen ku cekik dia", character: "Maverick" },
        ]
      },
      {
        question: "Bububmu marah sama kamu!",
        answers: [
          { text: "Ga terima, main tangan (pukul)", character: "Maverick" },
          { text: "Berusaha buat ngehibur dia sambil 'ya maap :'(", character: "Xen" },
          { text: "Marahin balik, ga lama kemudian pasti minta maaf", character: "Eric" },
          { text: "Diem sampe dia udah berhenti emosi, ga lama kemudian 'sudah marahnya? maaf ya..'", character: "Alex" },
        ]
      }
    ];

    const results = {
      Alex: "Kamu adalah orang yang kalem dan penuh pengertian. Kamu lebih memilih jalur damai, sabar, dan penyayang. Dalam hubungan, kamu sangat peduli dan ingin menjadi pasangan terbaik.",
      Xen: "Kamu adalah orang yang freaky, usil, dan CLINGY! Tapi justru itu yang bikin kamu seru dan dicintai. Kamu juga to the point dan percaya diri banget soal cinta!",
      Eric: "Kamu terlihat cuek dan kadang galak, tapi sebenernya kamu perhatian dan suka kasih effort kecil yang bermakna. Kamu juga suka ngajak main dan butuh pasangan yang bisa diajak seru-seruan.",
      Maverick: "Kamu adalah definisi BLACK FLAG. Kasar, dominan, dan cuek. Tapi ke orang yang kamu sayang, kamu bisa sangat protektif dan bucin diam-diam."
    };

    let currentQuestion = 0;
    let scores = { Alex: 0, Xen: 0, Eric: 0, Maverick: 0 };

    function startQuiz() {
      document.getElementById('start-screen').style.display = 'none';
      document.getElementById('quiz-screen').style.display = 'block';
      showQuestion();
    }

    function showQuestion() {
      const q = quizData[currentQuestion];
      const quizBox = document.getElementById('quiz-box');
      quizBox.innerHTML = `<div class="question-box"><h2>${q.question}</h2></div>` +
        q.answers.map((a, i) => `<div class="answer" onclick="selectAnswer('${a.character}')">${a.text}</div>`).join('');
    }

    function selectAnswer(character) {
      scores[character]++;
      currentQuestion++;
      if (currentQuestion < quizData.length) {
        showQuestion();
      } else {
        showResult();
      }
    }

    function showResult() {
      document.getElementById('quiz-screen').style.display = 'none';
      document.getElementById('result-screen').style.display = 'block';
      const result = Object.entries(scores).sort((a,b) => b[1] - a[1])[0][0];
      document.getElementById('result-text').innerText = results[result];
    }

    document.getElementById('start-screen').style.display = 'block';
  </script></body>
</html>
