# LIVE 13220821 — OMNIA r3

443 descriptions de contrats enrichies, dont 395 avec réputation de base numérique vérifiée entre variantes. 19 récapitulatifs natifs de paiement conservés. Les quantités calculées côté contrat restent variables. Aucun XP indépendant inventé ; aucune formule de partage en groupe supposée.

SHA-256 global.ini : 04da731b9f40faa62f79297164bb201d6d8e848c11411b25c7975e5563a098aa

## Sources

- Référence anglaise exacte et manifeste : reference.json et reference.ini.
- Faits du DataCore non chiffré : mission-facts.json ; extraction Windows https://github.com/madoredylan01-debug/omnia-link/actions/runs/45022677541
- Lecteur Apache-2.0 : https://github.com/Osiris-DevWorks/smart-citizen/tree/0d619d18987e7d5d6d581054a5e7f757a6164c56 ; aucun contournement de chiffrement.
- Base française Dymerz MIT : e497c66dbcdcb15d187c1477e1f3126a95b22100 ; notices jointes.
- Données Star Citizen © Cloud Imperium Games. Projet communautaire non officiel.

## Validation en jeu encore nécessaire

Jeu fermé : cliquer Mettre à jour dans OMNIA LINK 0.8.7. Relancer LIVE normalement. Ouvrir des contrats disponibles dans le mobiGlas ; ne pas accepter de mission uniquement pour ce test. Capturer volontairement uniquement la description de mission, avec son titre et son paiement.

Exemples de clés : Covalex_Delivery_Stanton_Medium_Desc_001 (+100 points Covalex) ; bhg_bounty_desc_Rockcracker_Zone1_001 (+150 points Guilde, piste Chasse à la prime) ; EckhartSecurity_Defend_E_Desc_001 (+500 points, piste Sécurité) ; RedWind_HaulCargo_MultiToSingle_desc_01 (valeur non déterminée entre variantes). La liste complète figure dans mission-enrichments.json.

Critères : bloc INFOS OMNIA lisible en fin de description, objectifs et variables d’origine conservés, aucune balise brute, défilement possible ; une récompense variable ne doit pas être annoncée fixe. Comparer la capture aux faits et aux variantes de la clé ; une valeur serveur différente exige une investigation et ne doit pas être masquée. Aucun gain effectif après accomplissement n’a été mesuré.

Cette révision n’est pas déclarée validée visuellement en jeu. Aucun changement PTU/EPTU, aucune modification de l’application, aucun installateur.
