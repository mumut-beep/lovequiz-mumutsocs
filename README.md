<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Quiz OC Mumut</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #d6f5d6;
      margin: 0;
      padding: 0;
    }
    .container {
      max-width: 600px;
      margin: auto;
      padding: 20px;
    }
    .question-box {
      background-color: #96c896;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 10px;
      font-weight: bold;
    }
    .answers button {
      display: block;
      width: 100%;
      margin: 10px 0;
      padding: 10px;
      font-size: 16px;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      background-color: #bce3bc;
    }
    .start-screen, .result-screen {
      text-align: center;
      padding: 40px;
    }
    #quiz, #result {
      display: none;
    }
  </style>
</head>
<body>
  <div class="container">
    <div id="start" class="start-screen">
      <h2>kamu mirip OC-nya mumut yang siapa yach?</h2>
      <button onclick="startQuiz()">Start</button>
    </div>
    <div id="quiz"></div>
    <div id="result" class="result-screen"></div>
  </div>
  <script>
    const quizData = [
      {
        question: "kamu kalo punya crush biasanya ngapain?",
        answers: [
          { text: "biasa aja, memilih jalur langit yaitu doain dia aja", oc: "Alex" },
          { text: "langsung pamer ke temen, ajakin dia kenalan, bahkan godain dia \"to the point aja lah\"", oc: "Xen" },
          { text: "ngasih dia jajan, hadiah kecil, atau oleh oleh, berharap dia notice kamu", oc: "Eric" },
          { text: "pengen ku cekik dia", oc: "Maverick" }
        ]
      },
      {
        question: "kamu kalo sama pasangan biasanya ngapain aja??",
        answers: [
          { text: "ngobrol, curhat, saling menyayangi, seperti couple sehat", oc: "Alex" },
          { text: "bermesra-mesraan, cuddling, flirting, ciuman, couple freaky deh", oc: "Xen" },
          { text: "ngedate, pergi kemana mana bareng, nonton bioskop", oc: "Eric" },
          { text: "pokoknya selama pasangan nurut, hubungan jadi baik", oc: "Maverick" }
        ]
      },
      {
        question: "bububmu lagi freaky dan godain kamu, responmu gimana?",
        answers: [
          { text: "gas aja ga si", oc: "Xen" },
          { text: "gas, cuman ga sampe lewati batas", oc: "Eric" },
          { text: "tolak dengan lembut", oc: "Alex" },
          { text: "kasur.", oc: "Maverick" }
        ]
      },
      {
        question: "bububmu marah sama kamu!",
        answers: [
          { text: "ga terima, main tangan (pukul)", oc: "Maverick" },
          { text: "berusaha buat ngehibur dia sambil \"ya maap :(\"", oc: "Xen" },
          { text: "marahin balik, ga lama kemudian pasti minta maap", oc: "Eric" },
          { text: "diem sampe dia udah berhenti emosi, ga lama kemudian \"sudah marahnya? maaf ya..\"", oc: "Alex" }
        ]
      }
    ];

    const results = {
      "Xen": "Kamu adalah orang yang freaky, clingy, dan dirty minded. Tapi kamu juga penuh semangat dan gampang bikin suasana jadi hidup. Kalau udah nyaman sama seseorang, kamu bisa jadi pasangan paling mesra dan lucu!",
      "Alex": "Kamu adalah sosok tenang, penyayang, dan pengertian. Terlihat dingin dari luar, tapi perhatian banget dan rela ngalah demi orang yang disayang. Kamu pasangan ideal yang dewasa dan sabar.",
      "Eric": "Kamu terlihat cool dan agak cuek, tapi aslinya gampang baper dan perhatian. Kamu suka nunjukin rasa sayang lewat hal kecil kayak traktir atau ngajak main bareng. Agak badut tapi manis.",
      "Maverick": "Kamu tipe black flag: dominan, misterius, dan kadang kasar. Tapi kamu punya sisi posesif yang berarti kamu sangat protektif ke orang yang kamu sayang. Di balik kesan galakmu, ada rasa sayang yang dalam."
    };

    let currentQuestion = 0;
    const score = {
      "Xen": 0,
      "Alex": 0,
      "Eric": 0,
      "Maverick": 0
    };

    function startQuiz() {
      document.getElementById("start").style.display = "none";
      document.getElementById("quiz").style.display = "block";
      showQuestion();
    }

    function showQuestion() {
      const quizEl = document.getElementById("quiz");
      const q = quizData[currentQuestion];
      quizEl.innerHTML = `<div class='question-box'><p>${q.question}</p></div><div class='answers'>`;
      q.answers.forEach((a, i) => {
        quizEl.innerHTML += `<button onclick='selectAnswer("${a.oc}")'>${a.text}</button>`;
      });
      quizEl.innerHTML += `</div>`;
    }

    function selectAnswer(oc) {
      score[oc]++;
      currentQuestion++;
      if (currentQuestion < quizData.length) {
        showQuestion();
      } else {
        showResult();
      }
    }

    function showResult() {
      document.getElementById("quiz").style.display = "none";
      document.getElementById("result").style.display = "block";
      let final = Object.entries(score).sort((a, b) => b[1] - a[1])[0][0];
      document.getElementById("result").innerHTML = `<h2>Kamu mirip ${final}!</h2><p>${results[final]}</p>`;
    }
  </script>
</body>
</html>
