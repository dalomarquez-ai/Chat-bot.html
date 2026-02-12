<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Coach Emocional</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f2f2f2;
}

.chat-container {
  display: flex;
  flex-direction: column;
  height: 100vh;
}

#chat {
  flex: 1;
  padding: 15px;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
}

.message {
  margin: 8px 0;
  padding: 10px 15px;
  border-radius: 18px;
  max-width: 75%;
}

.user {
  background: #007bff;
  color: white;
  align-self: flex-end;
}

.bot {
  background: #e4e6eb;
  color: black;
  align-self: flex-start;
}

.input-container {
  display: flex;
  padding: 10px;
  background: white;
  border-top: 1px solid #ccc;
}

input {
  flex: 1;
  padding: 10px;
  border-radius: 20px;
  border: 1px solid #ccc;
}

button {
  margin-left: 10px;
  padding: 10px 15px;
  border-radius: 20px;
  border: none;
  background: #007bff;
  color: white;
}
</style>
</head>

<body>

<div class="chat-container">
  <div id="chat"></div>

  <div class="input-container">
    <input type="text" id="userInput" placeholder="Cuéntame qué te preocupa...">
    <button onclick="sendMessage()">Enviar</button>
  </div>
</div>

<script>

function sendMessage() {
  var input = document.getElementById("userInput");
  var text = input.value;

  if (text.trim() === "") return;

  addMessage(text, "user");
  input.value = "";

  setTimeout(function() {
    var response = generateResponse(text.toLowerCase());
    addMessage(response, "bot");
  }, 400);
}

function addMessage(text, sender) {
  var chat = document.getElementById("chat");
  var message = document.createElement("div");

  message.className = "message " + sender;
  message.innerText = text;

  chat.appendChild(message);
  chat.scrollTop = chat.scrollHeight;
}

function generateResponse(text) {

  if (text.indexOf("triste") !== -1 || text.indexOf("solo") !== -1) {
    return "Entiendo cómo te sientes. Intenta hoy hacer una pequeña acción positiva, como caminar 10 minutos o hablar con alguien cercano.";
  }

  if (text.indexOf("ansiedad") !== -1 || text.indexOf("estres") !== -1) {
    return "Respira 4 segundos, mantén 4, suelta en 6. Repite 5 veces. Luego identifica qué parte de esto sí puedes controlar.";
  }

  if (text.indexOf("cansado") !== -1) {
    return "Tu cuerpo puede estar pidiendo descanso. Intenta desconectar 20 minutos sin pantallas.";
  }

  if (text.indexOf("motivado") !== -1 || text.indexOf("desmotivado") !== -1) {
    return "La motivación llega después de empezar. Haz una tarea pequeña ahora mismo.";
  }

  return "Cuéntame un poco más para poder ayudarte mejor.";
}

</script>

</body>
</html>
