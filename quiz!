<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Kamu Mirip OC Siapa?</title>
  <style>
    body {
      background-color: #d0f0c0;
      font-family: 'Arial', sans-serif;
      text-align: center;
      padding: 20px;
      color: #333;
    }
    .quiz-box {
      background: white;
      padding: 20px;
      border-radius: 16px;
      max-width: 700px;
      margin: auto;
      box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    }
    h2 { color: #2d6a4f; }
    .question { margin-bottom: 20px; font-weight: bold; }
    button {
      padding: 10px 20px;
      margin: 10px;
      border: none;
      border-radius: 8px;
      background-color: #95d5b2;
      color: white;
      cursor: pointer;
      font-size: 15px;
      display: block;
      width: 100%;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
    }
    #result { margin-top: 30px; font-size: 1.2em; font-weight: bold; }
    .oc-desc { text-align: left; margin-top: 20px; }
  </style>
</head>
<body>
  <div class="quiz-box">
    <h2>Quiz: Kamu Mirip OC Siapa?</h2>
    <div id="quiz">
      <div class="question" id="question"></div>
      <div id="answers"></div>
    </div>
    <div id="result"></div>
  </div>

  <script>
    const questions = [
      {
        q: "Kamu kalo punya crush biasanya ngapain?",
        answers: [
          { text: "Biasa aja, memilih jalur langit yaitu doain dia aja", oc: "Alex" },
          { text: "Langsung pamer ke temen, ajakin dia kenalan, bahkan godain dia \"to the point aja lah\"", oc: "Xen" },
          { text: "Ngasih dia jajan, hadiah kecil, atau oleh-oleh, berharap dia notice kamu", oc: "Eric" },
          { text: "Gamau ngaku kalo punya crush, padahal obsesi berat sama dia jir", oc: "Maverick" }
        ]
      },
      {
        q: "Hey tau ga si? Crushmu suka kamu balik loh!",
        answers: [
          { text: "\"Oh, ok\"", oc: "Alex" },
          { text: "\"MASA?! HOREEE, GAS KAN\"", oc: "Xen" },
          { text: "\"Jangan bohong deh, ga lucu... masa?\"", oc: "Eric" },
          { text: "\"Fans itu\"", oc: "Maverick" }
        ]
      },
      {
        q: "Kamu kalo sama pasangan biasanya ngapain?",
        answers: [
          { text: "Berusaha jadi yang terbaik buatnya, always jadi pendengar", oc: "Alex" },
          { text: "CLINGY ABIES, goda-godain dia melulu, hobi ngajakin mesra", oc: "Xen" },
          { text: "Yapping melulu, selalu ngajakin dia mabar njay", oc: "Eric" },
          { text: "Goda dan nempel mulu juga (freaky)", oc: "Maverick" }
        ]
      },
      {
        q: "Kalo bububmu ngambek sama kamu, kamu ngapain?",
        answers: [
          { text: "Diemin dia dulu, lalu: \"kamu udah selesai marahnya? maaf ya kalo ada salah..\"", oc: "Alex" },
          { text: "Berusaha hibur & gangguin dia: \"kamu marah karna apaa, maapin aku peliz\"", oc: "Xen" },
          { text: "\"Bisa berhenti marah dan kasih tau kenapa kamu ngambek ga, ngerepotin tau\"", oc: "Maverick" },
          { text: "Diemin, tapi dikit-dikit nanya salahmu apa", oc: "Eric" }
        ]
      },
      {
        q: "Bububmu lagi freaky nih, responmu gimana?",
        answers: [
          { text: "Gas aja ga si", oc: "Xen" },
          { text: "Berusaha dingin, padahal aslinya mau banget", oc: "Eric" },
          { text: "Tolak dengan lembut", oc: "Alex" }
        ]
      },
      {
        q: "Bububmu ketahuan selingkuh! Omaigat",
        answers: [
          { text: "Marahin dia, pokoknya murka bingit", oc: "Maverick" },
          { text: "\"Uhm, aku juga sering gitu\"", oc: "Xen" },
          { text: "Ngambek", oc: "Eric" },
          { text: "Maafin dengan alasan jelas kenapa dia selingkuh", oc: "Alex" }
        ]
      },
      {
        q: "\"Kalo aku berubah jadi kecoak, kamu masih sayang aku ga?\"",
        answers: [
          { text: "\"Sayang ko! Asal aku juga jadi kecoak\"", oc: "Xen" },
          { text: "\"Gajelas\"", oc: "Eric" },
          { text: "\"Sorry, ku semprot pake baygon\"", oc: "Maverick" },
          { text: "\"Iya, sayang. Tapi kenapa harus kecoak?\"", oc: "Alex" }
        ]
      },
      {
        q: "Kamu mau punya bubub kaya gimana?",
        answers: [
          { text: "Apa adanya, tapi harus FREAKY🤤", oc: "Xen" },
          { text: "Cantik, seksi, menggoda, gyat zamn banyak mau lu", oc: "Maverick" },
          { text: "Apa adanya yang penting ga nakal", oc: "Alex" },
          { text: "Mboh, yang penting cantik", oc: "Eric" }
        ]
      },
      {
        q: "Menurutmu, kamu apa?",
        answers: [
          { text: "Orang biasa", oc: "Alex" },
          { text: "Grin pleg", oc: "Eric" },
          { text: "Gwehj red pleg tau", oc: "Maverick" },
          { text: "Raja iblis", oc: "Xen" }
        ]
      },
      {
        q: "Menurutmu, kamu orangnya kaya gimana?",
        answers: [
          { text: "Dingin diluar, hangat didalam", oc: "Alex" },
          { text: "Asik diluar, freaky didalam", oc: "Xen" },
          { text: "Innocent diluar, freaky didalam", oc: "Maverick" }
        ]
      }
    ];

    const scores = { Alex: 0, Xen: 0, Eric: 0, Maverick: 0 };
    let index = 0;

    const questionBox = document.getElementById("question");
    const answerBox = document.getElementById("answers");
    const resultBox = document.getElementById("result");

    function showQuestion() {
      if (index < questions.length) {
        const current = questions[index];
        questionBox.innerText = current.q;
        answerBox.innerHTML = "";
        current.answers.forEach(answer => {
          const btn = document.createElement("button");
          btn.innerText = answer.text;
          btn.onclick = () => {
            scores[answer.oc]++;
            index++;
            showQuestion();
          };
          answerBox.appendChild(btn);
        });
      } else {
        showResult();
      }
    }

    function showResult() {
      document.getElementById("quiz").style.display = "none";
      const maxScore = Math.max(...Object.values(scores));
      const oc = Object.keys(scores).find(key => scores[key] === maxScore);
      let desc = "";

      if (oc === "Xen") {
        desc = `
          <div class="oc-desc">
            <h3>— Xen Vince Reviano Rachel</h3>
            <p>1. Kamu adalah orang yang usil, ngeselin, FREAKY BGT, dan dirty minded.<br>
            2. Terlalu clingy sama orang yang sudah dianggap nyaman.<br>
            3. Kepedean.</p>
          </div>
        `;
      } else if (oc === "Alex") {
        desc = `
          <div class="oc-desc">
            <h3>— Alejandro Lorenzo Alex Amberlynn</h3>
            <p>1. Kamu adalah orang yang sungguh dingin, padahal di dalam perhatian dan caring.<br>
            2. Selalu berusaha jadi yang terbaik.<br>
            3. Ga peduli kekurangan, yang penting cinta.</p>
          </div>
        `;
      } else if (oc === "Eric") {
        desc = `
          <div class="oc-desc">
            <h3>— Eric HarperWood Theodore</h3>
            <p>1. Berusaha dingin, padahal hatimu lembut.<br>
            2. Suka jadi badut, perhatian ke orang yang deket.<br>
            3. Keras di luar, lembut di dalam, pengen disayang.</p>
          </div>
        `;
      } else if (oc === "Maverick") {
        desc = `
          <div class="oc-desc">
            <h3>— Camden Maverick Maximilian</h3>
            <p>1. Kamu terlihat kasar dan jahat, tapi juga freaky!<br>
            2. Egois, sering mikirin diri sendiri.<br>
            3. Kasar ke orang lain, tapi lembut ke orang tersayang. Kadang ga terima kalau mereka marah ke kamu.</p>
          </div>
        `;
      }

      resultBox.innerHTML = `Kamu mirip: <strong>${oc}</strong>! ${desc}`;
    }

    showQuestion();
  </script>
</body>
</html>
