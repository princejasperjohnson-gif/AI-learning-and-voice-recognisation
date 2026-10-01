<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<!-- Basic browser security policy -->
<meta http-equiv="Content-Security-Policy"
      content="default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; connect-src 'self';">

<title>OneLink AI - Indian Language Assistant</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #eef4ff, #ffffff);
    color: #172033;
    min-height: 100vh;
}

header {
    background: #172554;
    color: white;
    padding: 20px;
    text-align: center;
}

header h1 {
    font-size: 30px;
}

header p {
    margin-top: 8px;
    opacity: 0.9;
}

nav {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
    padding: 15px;
    background: white;
    box-shadow: 0 2px 8px rgba(0,0,0,0.08);
}

nav button {
    border: none;
    padding: 12px 18px;
    border-radius: 8px;
    background: #e8eefc;
    cursor: pointer;
    font-weight: bold;
}

nav button:hover {
    background: #cddcff;
}

.container {
    max-width: 1100px;
    margin: 30px auto;
    padding: 20px;
}

.section {
    display: none;
}

.section.active {
    display: block;
}

.card {
    background: white;
    border-radius: 16px;
    padding: 25px;
    margin-bottom: 25px;
    box-shadow: 0 5px 20px rgba(0,0,0,0.08);
}

.card h2 {
    color: #172554;
    margin-bottom: 10px;
}

.card p {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-top: 15px;
    margin-bottom: 7px;
    font-weight: bold;
}

input, textarea, select {
    width: 100%;
    padding: 13px;
    border: 1px solid #cbd5e1;
    border-radius: 8px;
    font-size: 15px;
}

textarea {
    min-height: 130px;
    resize: vertical;
}

button.primary {
    margin-top: 15px;
    background: #2563eb;
    color: white;
    border: none;
    padding: 13px 20px;
    border-radius: 8px;
    cursor: pointer;
    font-weight: bold;
}

button.primary:hover {
    background: #1d4ed8;
}

button.voice {
    background: #16a34a;
}

button.voice:hover {
    background: #15803d;
}

.output {
    margin-top: 20px;
    padding: 18px;
    background: #f1f5f9;
    border-radius: 10px;
    white-space: pre-wrap;
    min-height: 80px;
}

.language-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 10px;
    margin-top: 15px;
}

.language {
    padding: 12px;
    background: #f8fafc;
    border: 1px solid #dbeafe;
    border-radius: 8px;
}

.warning {
    margin-top: 20px;
    padding: 15px;
    border-radius: 8px;
    background: #fff7ed;
    border-left: 5px solid #f97316;
}

footer {
    text-align: center;
    padding: 25px;
    margin-top: 30px;
    background: #172554;
    color: white;
}

@media(max-width:600px) {
    header h1 {
        font-size: 23px;
    }

    .container {
        padding: 10px;
    }

    .card {
        padding: 18px;
    }
}
</style>
</head>

<body>

<header>
    <h1>🌐 OneLink AI</h1>
    <p>AI Prompt Engineer • Indian Language Translator • Voice Assistant</p>
</header>

<nav>
    <button onclick="showSection('prompt')">
        🤖 AI Prompt Engineer
    </button>

    <button onclick="showSection('translator')">
        🌐 Translator
    </button>

    <button onclick="showSection('voice')">
        🎙️ Voice Assistant
    </button>
</nav>

<div class="container">

<!-- ================= PROMPT ENGINEER ================= -->

<section id="prompt" class="section active">

<div class="card">

<h2>🤖 AI Prompt Engineer</h2>

<p>
Create a clear AI prompt from your requirements.
</p>

<label>What do you want the AI to do?</label>

<textarea id="goal"
placeholder="Example: Create a website for a multilingual AI assistant"></textarea>

<label>AI Role</label>

<input id="role"
placeholder="Example: Expert software developer">

<label>Output Format</label>

<input id="format"
placeholder="Example: HTML, Python and explanation">

<button class="primary" onclick="generatePrompt()">
Generate AI Prompt
</button>

<div id="promptOutput" class="output"></div>

</div>

<div class="card">

<h2>🔐 Security Reminder</h2>

<p>
Never enter passwords, PINs, OTPs, banking information,
private keys or other confidential information into prompts.
</p>

</div>

</section>


<!-- ================= TRANSLATOR ================= -->

<section id="translator" class="section">

<div class="card">

<h2>🌐 Indian Language Translator</h2>

<p>
Select a source and target language and enter your text.
</p>

<label>Source Language</label>

<select id="sourceLanguage">

<option value="auto">Auto Detect</option>

<option>Assamese</option>
<option>Bengali</option>
<option>Bodo</option>
<option>Dogri</option>
<option>Gujarati</option>
<option>Hindi</option>
<option>Kannada</option>
<option>Kashmiri</option>
<option>Konkani</option>
<option>Maithili</option>
<option>Malayalam</option>
<option>Manipuri</option>
<option>Marathi</option>
<option>Nepali</option>
<option>Odia</option>
<option>Punjabi</option>
<option>Sanskrit</option>
<option>Santali</option>
<option>Sindhi</option>
<option>Tamil</option>
<option>Telugu</option>
<option>Urdu</option>

</select>


<label>Target Language</label>

<select id="targetLanguage">

<option>Hindi</option>
<option>Tamil</option>
<option>Telugu</option>
<option>Malayalam</option>
<option>Kannada</option>
<option>Marathi</option>
<option>Bengali</option>
<option>Gujarati</option>
<option>Punjabi</option>
<option>Odia</option>
<option>Assamese</option>
<option>Bodo</option>
<option>Dogri</option>
<option>Kashmiri</option>
<option>Konkani</option>
<option>Maithili</option>
<option>Manipuri</option>
<option>Nepali</option>
<option>Sanskrit</option>
<option>Santali</option>
<option>Sindhi</option>
<option>Urdu</option>

</select>


<label>Enter Text</label>

<textarea id="translateText"
maxlength="5000"
placeholder="Type or paste your text here..."></textarea>


<button class="primary" onclick="translateText()">
Translate
</button>

<button class="primary voice"
onclick="startTranslationVoice()">
🎙️ Speak
</button>

<div id="translationOutput" class="output">
Translation will appear here.
</div>

</div>


<div class="card">

<h2>🇮🇳 Supported Languages</h2>

<div class="language-grid">

<div class="language">Assamese</div>
<div class="language">Bengali</div>
<div class="language">Bodo</div>
<div class="language">Dogri</div>
<div class="language">Gujarati</div>
<div class="language">Hindi</div>
<div class="language">Kannada</div>
<div class="language">Kashmiri</div>
<div class="language">Konkani</div>
<div class="language">Maithili</div>
<div class="language">Malayalam</div>
<div class="language">Manipuri</div>
<div class="language">Marathi</div>
<div class="language">Nepali</div>
<div class="language">Odia</div>
<div class="language">Punjabi</div>
<div class="language">Sanskrit</div>
<div class="language">Santali</div>
<div class="language">Sindhi</div>
<div class="language">Tamil</div>
<div class="language">Telugu</div>
<div class="language">Urdu</div>

</div>

</div>

</section>


<!-- ================= VOICE ASSISTANT ================= -->

<section id="voice" class="section">

<div class="card">

<h2>🎙️ Multilingual Voice Assistant</h2>

<p>
Speak in your selected language and receive a spoken response.
</p>

<label>Choose Language</label>

<select id="voiceLanguage">

<option value="hi-IN">Hindi</option>
<option value="ta-IN">Tamil</option>
<option value="te-IN">Telugu</option>
<option value="ml-IN">Malayalam</option>
<option value="kn-IN">Kannada</option>
<option value="bn-IN">Bengali</option>
<option value="mr-IN">Marathi</option>
<option value="gu-IN">Gujarati</option>
<option value="pa-IN">Punjabi</option>
<option value="or-IN">Odia</option>
<option value="en-IN">English</option>

</select>

<button class="primary voice"
onclick="startVoiceAssistant()">

🎙️ Start Speaking

</button>

<label>Your Message</label>

<textarea id="voiceText"
placeholder="Your speech will appear here..."></textarea>

<button class="primary" onclick="assistantReply()">
Ask AI
</button>

<button class="primary voice" onclick="speakAnswer()">
🔊 Read Answer
</button>

<div id="assistantOutput" class="output">
Your assistant response will appear here.
</div>

</div>


<div class="card">

<h2>🛡️ Safety</h2>

<p>
This assistant should not be used to request or store passwords,
PINs, OTPs, banking credentials or other confidential information.
</p>

</div>

</section>

</div>


<footer>

<p>OneLink AI © 2026</p>

<p>
Multilingual • AI Assisted • Privacy Focused
</p>

</footer>


<script>

/* ================= SECTION NAVIGATION ================= */

function showSection(sectionName) {

    document.querySelectorAll(".section").forEach(section => {
        section.classList.remove("active");
    });

    document.getElementById(sectionName).classList.add("active");
}


/* ================= AI PROMPT ENGINEER ================= */

function generatePrompt() {

    const goal =
        document.getElementById("goal").value.trim();

    const role =
        document.getElementById("role").value.trim();

    const format =
        document.getElementById("format").value.trim();

    if (!goal) {
        alert("Please enter what you want the AI to do.");
        return;
    }

    const finalRole =
        role || "an expert AI assistant";

    const finalFormat =
        format || "a clear and structured answer";

    const prompt = `You are ${finalRole}.

TASK:
${goal}

REQUIREMENTS:
- Understand the user's intended language.
- Give accurate and easy-to-understand information.
- Ask for clarification when the request is genuinely ambiguous.
- Do not request or expose passwords, PINs, OTPs, API keys or private credentials.
- Protect user privacy.
- Do not invent information.
- Clearly identify uncertainty when necessary.

OUTPUT FORMAT:
${finalFormat}

LANGUAGE:
Respond in the user's selected or requested language.`;

    document.getElementById("promptOutput").textContent = prompt;
}


/* ================= TRANSLATOR ================= */

async function translateText() {

    const text =
        document.getElementById("translateText").value.trim();

    const source =
        document.getElementById("sourceLanguage").value;

    const target =
        document.getElementById("targetLanguage").value;

    const output =
        document.getElementById("translationOutput");

    if (!text) {
        output.textContent = "Please enter some text.";
        return;
    }

    output.textContent = "Translating...";

    /*
      This calls your Python backend.

      Your Flask application should provide:

      POST /api/translate

      Example JSON:
      {
        text: "...",
        source: "auto",
        target: "Tamil"
      }
    */

    try {

        const response = await fetch("/api/translate", {

            method: "POST",

            headers: {
                "Content-Type": "application/json"
            },

            body: JSON.stringify({
                text: text,
                source: source,
                target: target
            })

        });

        if (!response.ok) {
            throw new Error("Translation request failed");
        }

        const data = await response.json();

        output.textContent =
            data.translatedText ||
            data.translation ||
            "No translation returned.";

    } catch (error) {

        output.textContent =
            "Translation service is not connected. " +
            "Connect this page to the Python backend.";

    }
}


/* ================= VOICE INPUT ================= */

function startTranslationVoice() {

    const SpeechRecognition =
        window.SpeechRecognition ||
        window.webkitSpeechRecognition;

    if (!SpeechRecognition) {

        alert(
            "Speech recognition is not supported by this browser."
        );

        return;
    }

    const recognition =
        new SpeechRecognition();

    const language =
        document.getElementById("voiceLanguage").value;

    recognition.lang = language;

    recognition.interimResults = false;

    recognition.maxAlternatives = 1;

    recognition.start();

    recognition.onresult = function(event) {

        const text =
            event.results[0][0].transcript;

        document.getElementById("translateText").value =
            text;
    };

    recognition.onerror = function() {

        alert("Voice recognition could not be started.");

    };
}


/* ================= VOICE ASSISTANT ================= */

function startVoiceAssistant() {

    const SpeechRecognition =
        window.SpeechRecognition ||
        window.webkitSpeechRecognition;

    if (!SpeechRecognition) {

        alert(
            "Speech recognition is not supported by this browser."
        );

        return;
    }

    const recognition =
        new SpeechRecognition();

    recognition.lang =
        document.getElementById("voiceLanguage").value;

    recognition.interimResults = false;

    recognition.maxAlternatives = 1;

    recognition.start();

    recognition.onresult = function(event) {

        const text =
            event.results[0][0].transcript;

        document.getElementById("voiceText").value =
            text;

    };

    recognition.onerror = function() {

        alert("Could not recognize your voice.");

    };
}


/* ================= AI ASSISTANT ================= */

async function assistantReply() {

    const message =
        document.getElementById("voiceText").value.trim();

    const output =
        document.getElementById("assistantOutput");

    if (!message) {

        output.textContent =
            "Please enter or speak a message.";

        return;
    }

    output.textContent =
        "Thinking...";

    try {

        const response = await fetch(
            "/api/assistant",
            {
                method: "POST",

                headers: {
                    "Content-Type": "application/json"
                },

                body: JSON.stringify({
                    message: message
                })
            }
        );

        if (!response.ok) {
            throw new Error("Assistant request failed");
        }

        const data =
            await response.json();

        output.textContent =
            data.response ||
            "No response received.";

    } catch (error) {

        /*
          Safe local fallback.
        */

        output.textContent =
            "Your message was received. " +
            "Connect the Python AI backend to enable " +
            "full AI responses.";

    }
}


/* ================= TEXT TO SPEECH ================= */

function speakAnswer() {

    const text =
        document.getElementById("assistantOutput")
        .textContent;

    if (!text) {
        return;
    }

    if (!("speechSynthesis" in window)) {

        alert(
            "Text-to-speech is not supported by this browser."
        );

        return;
    }

    const speech =
        new SpeechSynthesisUtterance(text);

    speech.lang =
        document.getElementById("voiceLanguage").value;

    window.speechSynthesis.cancel();

    window.speechSynthesis.speak(speech);
}

</script>

</body>
</html>
