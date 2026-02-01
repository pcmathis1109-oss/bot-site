<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Bot interactif</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #e0f7fa;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    #chat-container {
      background: #ffffff;
      width: 350px;
      border-radius: 12px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
      padding: 10px;
      display: flex;
      flex-direction: column;
    }

    #chat {
      height: 300px;
      overflow-y: auto;
      border: 1px solid #ccc;
      border-radius: 8px;
      padding: 10px;
      margin-bottom: 10px;
      background: #f1f1f1;
    }

    .message {
      margin: 5px 0;
      padding: 6px 10px;
      border-radius: 15px;
      max-width: 80%;
      word-wrap: break-word;
    }

    .user {
      background: #81d4fa;
      align-self: flex-end;
    }

    .bot {
      background: #c5e1a5;
      align-self: flex-start;
    }

    input {
      width: 70%;
      padding: 5px;
      border-radius: 6px;
      border: 1px solid #ccc;
    }

    button {
      padding: 6px 10px;
      margin-left: 5px;
      border: none;
      border-radius: 6px;
      background: #26a69a;
      color: white;
      cursor: pointer;
    }

    button:hover {
      background: #00796b;
    }
  </style>
</head>
<body>

<div id="chat-container">
  <div id="chat"></div>
  <div style="display:flex;">
    <input id="msg" placeholder="Écris un message">
    <button onclick="send()">Envoyer</button>
  </div>
</div>

<script>
function send() {
  let msg = document.getElementById("msg").value.trim();
  if(msg === "") return;

  // Affiche le message de l'utilisateur
  let chat = document.getElementById("chat");
  let userDiv = document.createElement("div");
  userDiv.className = "message user";
  userDiv.innerText = msg;
  chat.appendChild(userDiv);

  // Réponse du bot
  let rep = "Je ne comprends pas 😅";

  msg = msg.toLowerCase();
  if(msg.includes("bonjour")) rep = "Bonjour 👋 ! Comment ça va ?";
  else if(msg.includes("salut")) rep = "Salut ! 😄";
  else if(msg.includes("aide")) rep = "Je suis là pour t’aider ! 😎";
  else if(msg.includes("merci")) rep = "Avec plaisir 😄";
  else if(msg.includes("comment ça va")) rep = "Ça va super, merci ! Et toi ?";
  else if(msg.includes("qui es-tu")) rep = "Je suis ton bot interactif 🤖";
  else if(msg.includes("quoi de neuf")) rep = "Pas grand-chose, je papote avec toi 😄";

  // Affiche la réponse du bot
  let botDiv = document.createElement("div");
  botDiv.className = "message bot";
  botDiv.innerText = rep;
  chat.appendChild(botDiv);

  // Scroll automatique
  chat.scrollTop = chat.scrollHeight;

  document.getElementById("msg").value = "";
}
</script>

</body>
</html>
