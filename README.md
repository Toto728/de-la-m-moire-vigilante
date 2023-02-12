# de-la-m-moire-vigilante
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Entrée de code Metamask</title>
  </head>
  <body>
    <h1>Entrée de code Metamask</h1>
    <form>
      <label for="code">Entrez votre code :</label>
      <input type="text" id="code" name="code">
      <br><br>
      <button id="submit-button">Soumettre</button>
    </form>
    <div id="message"></div>
    <script src="https://cdn.jsdelivr.net/npm/@metamask/inpage-provider@0.12.2/dist/inpage-provider.min.js"></script>
    <script>
      const messageDiv = document.getElementById('message');
      const submitButton = document.getElementById('submit-button');
      
      // Vérifier si Metamask est installé et activé
      if (typeof window.ethereum === 'undefined') {
        messageDiv.innerHTML = 'Metamask est requis pour utiliser cette page. Veuillez l\'installer et l\'activer.';
        submitButton.setAttribute('disabled', true);
      } else {
        // Demander l'autorisation à l'utilisateur pour accéder à son portefeuille Metamask
        window.ethereum.enable().then(() => {
          submitButton.addEventListener('click', () => {
            const code = document.getElementById('code').value;
            // Faire quelque chose avec le code entré
            messageDiv.innerHTML = 'Code soumis : ' + code;
          });
        });
      }
    </script>
  </body>
</html>
