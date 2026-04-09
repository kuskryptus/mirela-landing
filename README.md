# App Mirela Landing

Staticka landing page postavena na `Vue 3 + Vite`.

## Lokalny vyvoj

```bash
npm install
npm run dev
```

## Produkcny build

```bash
npm run build
```

Vysledok sa vytvori do priecinka `dist/`.

## Deploy na server s nginx

Nginx `root` ma smerovat na:

```bash
/var/www/mirela-landing
```

Na serveri je potrebne skopirovat obsah `dist/` do tejto cesty, nie cely zdrojovy projekt.

Priklad deploy kroku po naklonovani repozitara na server:

```bash
npm ci
npm run build
sudo mkdir -p /var/www/mirela-landing
sudo rsync -a --delete dist/ /var/www/mirela-landing/
sudo nginx -t
sudo systemctl reload nginx
```
