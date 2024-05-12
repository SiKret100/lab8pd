# Budowanie obrazu zawierającego dane SBOM
```docker buildx build --no-cache -f Dockerfile_classic -t dawidrut01/labtest:cla --sbom=true --provenance=mode=max --push .```
# Określenie zagrożenia na podatności
```docker scout cves dawidrut01/labtest:cla```

# Zagrożenia przed dokonaniem zmian package.json
<img width="816" alt="Screenshot 2024-05-12 at 16 56 57" src="https://github.com/SiKret100/lab8pd/assets/83550480/a721fbca-7939-42d2-93b2-a11d25f91c46">


# Dokonanie zmiany w pliku package.json
```
{
  "name": "weather",
  "version": "0.0.0",
  "private": true,
  "scripts": {
    "start": "node ./bin/www"
  },
  "dependencies": {
    "body-parser": "1.20.2",
    "cookie-parser": "1.4.6",
    "debug": "4.3.4",
    "ejs": "3.1.10",
    "express": "4.19.2",
    "morgan": "1.10.0",
    "pug": "3.0.2",
    "request": "2.88.2",
    "serve-favicon": "2.5.0",
    "lodash": "4.17.21",
    "json-schema": "0.4.0",
    "qs": "6.5.3",
    "tough-cookie": "4.1.3",
    "jsprim": "2.0.2"
  }
}
```

Zmiany w wersjach pakietów przeprowadziłem, kierując się opisami zagrożeń oraz informacjami o zależnościach z pliku package-lock.json. Na przykład, samo zaktualizowanie wersji pakietu `qs` w `dependencies` nie było wystarczające, gdyż pakiet `request` używał przestarzałej jego wersji. W związku z tym, zaktualizowałem również wersję `request` do nowszej. W podobny sposób postąpiłem z innymi identyfikowanymi zagrożeniami.

# Zagrożenia po dokonaniu zmian
<img width="821" alt="Screenshot 2024-05-12 at 16 54 05" src="https://github.com/SiKret100/lab8pd/assets/83550480/e1d0587f-df5b-41e1-8964-c430f25516e6">

