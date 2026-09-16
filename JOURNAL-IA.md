# Journal IA — Mini-TP 3

**Étudiant :** ETU002630 — Razafinjoelina Fitia Elie Evah

- Ligne diagnostiquée : `MainActivity.onCreate`, ligne 29, dans le paquet `mg.itu.cycledevie`.
- Cause : `findViewById` cherche `btnPartage`, mais le vrai layout déclare le bouton sous l’identifiant `btnPartager` ; la recherche ne fournit donc pas le bouton attendu.
- Verdict et correction : j’accepte le diagnostic s’il propose `R.id.btnPartager`, après avoir vérifié ce nom dans `activity_main.xml`.
