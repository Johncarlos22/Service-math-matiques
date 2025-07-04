<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Services de Mathématiques</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
        }
        header {
            background: #007bff;
            color: white;
            padding: 10px 0;
            text-align: center;
        }
        .container {
            width: 80%;
            margin: auto;
            overflow: hidden;
            padding: 20px;
            background: white;
        }
        button {
            background: #007bff;
            color: white;
            border: none;
            padding: 10px 20px;
            cursor: pointer;
        }
        button:hover {
            background: #0056b3;
        }
        form {
            margin-top: 20px;
        }
        label {
            display: block;
            margin: 10px 0 5px;
        }
        input, textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
        }
    </style>
</head>
<body>

<header>
    <h1>Bienvenue aux Services de Mathématiques</h1>
</header>

<div class="container">
    <h2>Nos Services</h2>
    <p>Nous offrons une aide complète en mathématiques, y compris :</p>
    <ul>
        <li>Tutorat individuel</li>
        <li>Aide aux devoirs</li>
        <li>Préparation aux examens</li>
    </ul>
    <p>Pour plus d'informations ou pour réserver un service, remplissez le formulaire ci-dessous :</p>
    
    <form action="mailto:carlosdedji95@gmail.com" method="post" enctype="text/plain">
        <label for="name">Votre nom :</label>
        <input type="text" id="name" name="name" required>

        <label for="email">Votre e-mail :</label>
        <input type="email" id="email" name="email" required>

        <label for="phone">Votre numéro de téléphone :</label>
        <input type="tel" id="phone" name="phone" required>

        <label for="file">Téléchargez votre fichier :</label>
        <input type="file" id="file" name="file" required>

        <button type="submit">Soumettre</button>
    </form>
</div>

</body>
</html>
