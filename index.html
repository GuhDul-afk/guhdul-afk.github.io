// Service worker : met en cache les fichiers de l'appli pour qu'elle
// s'ouvre même sans connexion. Pour index.html en particulier, on vérifie
// TOUJOURS la version en ligne en premier (réseau prioritaire) — le cache ne
// sert que de secours si le téléphone est hors-ligne. Ça évite de rester
// coincé sur une ancienne version après une mise à jour.
//
// IMPORTANT : à chaque modification de l'appli, incrémenter CACHE_NAME
// (v2, v3, ...) pour que le navigateur détecte que ce fichier a changé.
const CACHE_NAME = 'carnet-de-bord-v2';
const FILES_TO_CACHE = [
  './',
  './index.html',
  './manifest.json',
  './icon-192.png',
  './icon-512.png',
];

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open(CACHE_NAME).then((cache) => cache.addAll(FILES_TO_CACHE))
  );
  self.skipWaiting();
});

self.addEventListener('activate', (event) => {
  event.waitUntil(
    caches.keys().then((keys) =>
      Promise.all(keys.filter((k) => k !== CACHE_NAME).map((k) => caches.delete(k)))
    )
  );
  self.clients.claim();
});

self.addEventListener('fetch', (event) => {
  const isHtmlPage = event.request.mode === 'navigate' || event.request.url.endsWith('index.html');

  if(isHtmlPage){
    // Réseau prioritaire pour la page principale : toujours la dernière version si possible.
    event.respondWith(
      fetch(event.request)
        .then((res) => {
          const copy = res.clone();
          caches.open(CACHE_NAME).then((cache) => cache.put(event.request, copy));
          return res;
        })
        .catch(() => caches.match(event.request))
    );
  }else{
    // Cache prioritaire pour le reste (icônes, manifest) : ça change rarement.
    event.respondWith(
      caches.match(event.request).then((cached) => cached || fetch(event.request))
    );
  }
});
