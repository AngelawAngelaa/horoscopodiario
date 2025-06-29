
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Registro de Horóscopo Diario</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f0f4f8;
      padding: 20px;
    }
    .promo, .pago {
      background-color: #fff3cd;
      border: 1px solid #ffeeba;
      color: #856404;
      padding: 20px;
      max-width: 500px;
      margin: 0 auto 20px auto;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.05);
    }
    .promo h3, .pago h3 {
      margin-top: 0;
    }
    .cuenta {
      font-weight: bold;
      font-size: 18px;
      color: #d63384;
    }
    .btn-group {
      margin-top: 15px;
      display: flex;
      gap: 10px;
      flex-direction: column;
    }
    .btn-copy, .btn-whatsapp {
      padding: 10px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      color: white;
      text-align: center;
      text-decoration: none;
    }
    .btn-copy {
      background-color: #007bff;
    }
    .btn-copy:hover {
      background-color: #0056b3;
    }
    .btn-whatsapp {
      background-color: #25D366;
    }
    .btn-whatsapp:hover {
      background-color: #1da851;
    }
    form {
      background-color: white;
      padding: 20px;
      max-width: 500px;
      margin: auto;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    h2 {
      text-align: center;
    }
    label {
      display: block;
      margin-top: 15px;
      font-weight: bold;
    }
    input, select {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    .radio-group {
      display: flex;
      gap: 10px;
      margin-top: 5px;
    }
    .submit-btn {
      background-color: #4CAF50;
      color: white;
      padding: 10px;
      margin-top: 20px;
      border: none;
      cursor: pointer;
      width: 100%;
      font-size: 16px;
      border-radius: 5px;
    }
    .submit-btn:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>

  <div class="promo">
    <h3>✨ ¡Suscríbete a tu horóscopo diario!</h3>
    <p>Con esta promo, recibirás tu horóscopo personalizado cada mañana, directo a tu WhatsApp o correo.</p>
    <p><strong>Incluye:</strong></p>
    <ul>
      <li>✅ Predicción diaria según tu signo</li>
      <li>✅ Mensajes de energía y consejos espirituales</li>
      <li>✅ Rituales o tips según la energía del día</li>
    </ul>
    <p><strong>💸 Precio especial por tiempo limitado:</strong> <span style="color:#d63384;">$200 MXN por 30 días</span></p>
    <p>📩 ¡Escríbenos ahora y activa tu suscripción diaria!</p>
  </div>

  <div class="pago">
    <h3>💳 Datos para realizar el pago:</h3>
    <p>Realiza tu pago de <strong>$200 MXN</strong> a la siguiente cuenta:</p>
    <p>Cuenta CLABE: <span class="cuenta" id="clabe">638180000196043551</span></p>
    <p>Banco: <strong>Banco Nu</strong></p>

    <div class="btn-group">
      <button class="btn-copy" onclick="copiarCLABE()">📋 Copiar CLABE</button>
      <a class="btn-whatsapp" href="https://wa.me/522211659112?text=Hola,%20ya%20realicé%20mi%20pago%20para%20el%20horóscopo.%20Adjunto%20mi%20comprobante." target="_blank">
        📩 Enviar comprobante por WhatsApp
      </a>
    </div>

    <p style="margin-top:10px;">Una vez realizado el pago, completa el formulario abajo para activar tu horóscopo diario.</p>
  </div>

  <!-- Formulario con Formspree -->
  <form action="https://formspree.io/f/xdkzyvjd" method="POST">
    <h2>Registro para Horóscopo Diario</h2>

    <input type="hidden" name="_subject" value="Nuevo registro para horóscopo diario">

    <label for="nombre">Nombre completo:</label>
    <input type="text" id="nombre" name="nombre" required>

    <label>Sexo:</label>
    <div class="radio-group">
      <label><input type="radio" name="sexo" value="masculino" required> Masculino</label>
      <label><input type="radio" name="sexo" value="femenino" required> Femenino</label>
      <label><input type="radio" name="sexo" value="otro" required> Otro</label>
    </div>

    <label for="fecha">Fecha de nacimiento:</label>
    <input type="date" id="fecha" name="fecha" required>

    <label for="signo">Signo zodiacal:</label>
    <select id="signo" name="signo" required>
      <option value="">Selecciona tu signo</option>
      <option value="aries">Aries</option>
      <option value="tauro">Tauro</option>
      <option value="geminis">Géminis</option>
      <option value="cancer">Cáncer</option>
      <option value="leo">Leo</option>
      <option value="virgo">Virgo</option>
      <option value="libra">Libra</option>
      <option value="escorpio">Escorpio</option>
      <option value="sagitario">Sagitario</option>
      <option value="capricornio">Capricornio</option>
      <option value="acuario">Acuario</option>
      <option value="piscis">Piscis</option>
    </select>

    <label>¿Cómo deseas recibir tu horóscopo diario?</label>
    <div class="radio-group">
      <label><input type="radio" name="medio" value="correo" required> Correo electrónico</label>
      <label><input type="radio" name="medio" value="whatsapp" required> WhatsApp</label>
    </div>

    <label for="contacto">Correo electrónico o número de WhatsApp:</label>
    <input type="text" id="contacto" name="contacto" required placeholder="Ej. ejemplo@correo.com o +521234567890">

    <button type="submit" class="submit-btn">Registrarse</button>
  </form>

  <script>
    function copiarCLABE() {
      const clabe = document.getElementById("clabe").innerText;
      navigator.clipboard.writeText(clabe)
        .then(() => alert("CLABE copiada al portapapeles"))
        .catch(() => alert("Error al copiar CLABE"));
    }
  </script>

</body>
</html>
