PARTIE 1:

Question 1.1 donner la liste des en-têtes de la réponse HTTP du serveur.

HTTP/1.1 200 OK
Date: Sun, 15 Sep 2024 22:18:37 GMT
Connection: keep-alive
Keep-Alive: timeout=5
Transfer-Encoding: chunked


Question 1.2 donner la liste des en-têtes qui ont changé depuis la version précédente.


HTTP/1.1 200 OK
Content-Type: application/json
Date: Sun, 15 Sep 2024 22:21:58 GMT
Connection: keep-alive
Keep-Alive: timeout=5
Content-Length: 20

Il y a :
-Content-Type: application/json
-Content-Length: 20

qui se sont rajouté


Question 1.3 que contient la réponse reçue par le client ?

Le client ne reçoit aucune réponse, la page ne s'ouvre pas

Question 1.4 quelle est l’erreur affichée dans la console ? 

L'erreur adffcihé dans la console est l'erreur -4058

Question 1.5 donner le code de requestListener() modifié avec gestion d’erreur en async/await.

async function requestListener(_request, response) {
  try {
    const contents = await fs.readFile("index.html", "utf8");
    response.setHeader("Content-Type", "text/html");
    response.writeHead(200);
    response.end(contents);
  } catch (error) {
    console.error(error);
    response.setHeader("Content-Type", "text/plain");
    response.writeHead(500);
    response.end("Erreur 500");
  }
}

Question 1.6 indiquer ce que cette commande a modifié dans votre projet.

le dossier node_modules et le fichier package-lock.json on été ajouté

Question 1.7 quelles sont les différences entre les scripts http-dev et http-prod ?

Avec http-dev chaque changement dans server-http.mjs est sauvegarder et le serveurs et rafraichit alors qu'avec http-prod le serveur n'est pas actualier a chaque changment dans server-htpp.mjs

Question 1.8 donner les codes HTTP reçus par votre navigateur pour chacune des quatre pages précédentes.

Avec :
    -http://localhost:8000/index.html on a le code 200
    -http://localhost:8000/random.html on a le code 200
    -http://localhost:8000/ on a le code 404
    -http://localhost:8000/dont-exist on a le code 404


PARTIE 2:

Question 2.1 donner les URL des documentations de chacun des modules installés par la commande précédente.
    URL:
        -Express: https://expressjs.com
        -http-errors: https://github.com/jshttp/http-errors
        -loglevel: https://github.com/pimterry/loglevel
        -morgan: https://github.com/expressjs/morgan

Question 2.2 vérifier que les trois routes fonctionnent.

    Les 3 routes fonctionnent bien


Question 2.3 lister les en-têtes des réponses fournies par Express. Lesquelles sont nouvelles par rapport au serveur HTTP ?

-X-Powered-By: Express
-Accept-Ranges: bytes
-Cache-Control: public, max-age=0
-Last-Modified: Wed, 25 Sep 2024 02:31:33 GMT
-ETag: W/"eb-192270503a4"
-Content-Type: text/html; charset=UTF-8
-Content-Length: 235
    
Question 2.4 quand l’événement listening est-il déclenché ?

    L'évènement listening est déclenché quand le serveur passe en "on" c'est a dire quand on le lance.

Question 2.5 indiquer quelle est l’option (activée par défaut) qui redirige / vers /index.html ?

    c'est le paramètre ('static') qui renvoie automatiquement / vers /index.html (si il est présent)
