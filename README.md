<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>Site de Relacionamento</title>
  <style>
    body { margin:0; font-family:Arial,sans-serif; background:#0f172a; color:#fff; }
    .container { max-width:420px; margin:auto; min-height:100vh; display:flex; flex-direction:column; }
    header { padding:16px; text-align:center; background:#1e293b; font-weight:bold; font-size:18px; }
    .content { flex:1; padding:16px; }
    .btn { width:100%; padding:14px; margin-top:10px; background:#22c55e; border:none; border-radius:10px; font-size:16px; font-weight:bold; color:#000; }
    .btn.secondary { background:#38bdf8; }
    .card { background:#1e293b; padding:14px; border-radius:12px; margin-bottom:12px; }
    input { width:100%; padding:12px; margin-top:8px; border-radius:8px; border:none; }
    footer { padding:10px; text-align:center; font-size:12px; background:#020617; opacity:0.7; }
  </style>
</head>
<body>
<div class="container">
  <header>💬 Relacionamentos Online</header>

  <div class="content" id="home">
    <div class="card">
      <p>Converse, conheça pessoas e faça novas conexões.</p>
      <p><small>Plataforma exclusiva para celular</small></p>
      <button class="btn" onclick="showLogin()">Entrar</button>
      <button class="btn secondary" onclick="showRegister()">Criar Conta</button>
    </div>
  </div>

  <div class="content" id="login" style="display:none">
    <div class="card">
      <h3>Entrar</h3>
      <input id="loginUser" placeholder="Usuário" />
      <input id="loginPass" type="password" placeholder="Senha" />
      <button class="btn" onclick="showOnline()">Entrar</button>
    </div>
  </div>

  <div class="content" id="register" style="display:none">
    <div class="card">
      <h3>Criar Conta</h3>
      <input placeholder="Nome" />
      <input placeholder="Idade (18+)" />
      <input placeholder="Usuário" />
      <input type="password" placeholder="Senha" />
      <button class="btn" onclick="showOnline()">Criar Conta (100 créditos)</button>
    </div>
  </div>

  <div class="content" id="online" style="display:none">
    <div class="card">
      <h3>Usuários Online</h3>
      <p onclick="openChat('Maria')">🟢 Maria</p>
      <p onclick="openChat('Carlos')">🟢 Carlos</p>
      <p onclick="openChat('Ana')">🟢 Ana</p>
    </div>
    <button class="btn secondary" onclick="showCredits()">Comprar Créditos</button>
  </div>

  <div class="content" id="chat" style="display:none">
    <div class="card">
      <h3 id="chatUser">Chat</h3>
      <div id="messages" style="min-height:120px;font-size:14px"></div>
      <input id="msg" placeholder="Digite sua mensagem" />
      <button class="btn" onclick="sendMessage()">Enviar (1 crédito)</button>
      <button class="btn secondary" onclick="sendPhoto()">Enviar Foto (5 créditos)</button>
    </div>
  </div>

  <div class="content" id="credits" style="display:none">
    <div class="card">
      <h3>Comprar Créditos</h3>
      <p>Pix: <b>85 99664-0269</b></p>
      <p>Envie o comprovante pelo chat.</p>
      <button class="btn" onclick="notificarPagamento('Cliente','300 créditos')">Já paguei</button>
    </div>
  </div>

  <footer>© Plataforma Mobile • Uso exclusivo em celular</footer>
</div>

<script>
  const ADMIN_WHATSAPP = '5585920013984';

  function notificarPagamento(cliente, pacote) {
    const mensagem = `Novo pagamento Pix recebido%0ACliente: ${cliente}%0APacote: ${pacote}`;
    window.open(`https://wa.me/${ADMIN_WHATSAPP}?text=${mensagem}`, '_blank');
  }

  function hideAll() {
    ['home','login','register','online','chat','credits'].forEach(id => document.getElementById(id).style.display='none');
  }

  function showLogin() { hideAll(); document.getElementById('login').style.display='block'; }
  function showRegister() { hideAll(); document.getElementById('register').style.display='block'; }
  function showOnline() { hideAll(); document.getElementById('online').style.display='block'; }
  function openChat(user) { hideAll(); document.getElementById('chat').style.display='block'; document.getElementById('chatUser').innerText='Chat com '+user; }
  function showCredits() { hideAll(); document.getElementById('credits').style.display='block'; }

  let credits = 100;

  function sendMessage() {
    if (credits <= 0) { alert('Sem créditos'); return; }
    credits--;
    document.getElementById('messages').innerHTML += `<p>Você: ${msg.value}</p>`;
    msg.value = '';
  }

  function sendPhoto() {
    if (credits < 5) { alert('Créditos insuficientes'); return; }
    credits -= 5;
    document.getElementById('messages').innerHTML += '<p>📸 Foto enviada</p>';
  }
</script>
</body>
</html>
# lovechat
