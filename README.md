<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cambiar Contraseña - Instagram</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #fafafa;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            padding: 30px 20px;
            width: 320px;
            text-align: center;
        }

        .logo-container {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin-bottom: 25px;
        }

        .logo-container img {
            width: 80px;
            height: auto;
            margin-bottom: 10px; /* Separación entre imágenes */
        }

        h1 {
            font-size: 24px;
            margin-bottom: 25px;
        }

        input[type="password"] {
            width: 100%;
            padding: 10px;
            margin: 10px 0 15px;
            border: 1px solid #ccc;
            border-radius: 4px;
        }

        input[type="password"].error {
            border-color: red;
        }

        button {
            background-color: #0095f6;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 4px;
            cursor: pointer;
            width: 100%;
            font-size: 16px;
            margin-top: 10px;
        }

        button:hover {
            background-color: #007bbf;
        }

        .error-message {
            color: gray;
            font-size: 13px;
            text-align: left;
            margin-top: -10px;
            margin-bottom: 20px;
        }

        .success-message {
            color: green;
            font-size: 14px;
            margin-top: 15px;
        }

        ul {
            margin: 5px 0;
            padding-left: 20px;
            text-align: left;
        }

        li {
            margin-bottom: 5px;
        }
    </style>
</head>
<body>

<div class="container">
    <div class="logo-container">
        <img src="https://upload.wikimedia.org/wikipedia/commons/a/a5/Instagram_icon.png" alt="Instagram Icon">
        <img src="https://www.instagram.com/static/images/web/mobile_nav_type_logo.png/735145cfe0a4.png" alt="Instagram Logo">
    </div>
    <h1>Cambiar Contraseña</h1>
    <form id="changePasswordForm">
        <input type="password" id="newPassword" placeholder="Nueva Contraseña" required>
        <div id="errorMessage" class="error-message"></div>
        <div id="successMessage" class="success-message"></div>
        <button type="submit">Cambiar Contraseña</button>
    </form>
</div>

<script>
    const form = document.getElementById('changePasswordForm');
    const passwordInput = document.getElementById('newPassword');
    const errorMessage = document.getElementById('errorMessage');
    const successMessage = document.getElementById('successMessage');

    form.addEventListener('submit', function(event) {
        event.preventDefault();
        const password = passwordInput.value;
        const requirements = [
            { test: /.{8,}/, message: "Al menos 8 caracteres" },
            { test: /[0-9]/, message: "Incluir números" },
            { test: /[a-z]/, message: "Incluir letras minúsculas" },
            { test: /[A-Z]/, message: "Incluir letras mayúsculas" },
            { test: /[!@#$%^&*(),.?":{}|<>]/, message: "Incluir símbolos" },
        ];

        let valid = true;
        let messages = "<ul>";

        requirements.forEach(req => {
            if (!req.test.test(password)) {
                valid = false;
                messages += `<li>${req.message}</li>`;
            }
        });

        messages += "</ul>";

        if (valid) {
            errorMessage.innerHTML = "";
            passwordInput.classList.remove('error');
            successMessage.textContent = "Contraseña cambiada con éxito";
        } else {
            successMessage.textContent = "";
            errorMessage.innerHTML = messages;
            passwordInput.classList.add('error');
        }
    });
</script>

</body>
</html>
