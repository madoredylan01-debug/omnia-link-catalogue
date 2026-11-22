# LIVE 13220821 r5 — détails du contrat

Cette révision part du r4 fonctionnel. Le corps français, les variables et le BOM sont conservés. Le gestionnaire et les autres modules ne changent pas. Les différences concernent les blocs OMNIA des descriptions de missions.

## Informations livrées et niveau de preuve

| Information | Couverture / preuve |
|---|---|
| Distribution documentée | 3 412 définitions candidates. Documentation du mécanisme standard CIG croisée avec le caractère partageable et le résultat monétaire du build exact. |
| Exceptions explicites de distribution des crédits | Aucun réglage par contrat permettant de confirmer une exception trouvé ; aucun versement en serveur observé. Les événements et mécanismes non corroborés ne reçoivent pas artificiellement la règle standard. |
| Réputation | 3 155 candidates avec valeurs configurées vérifiables. 780 descriptions avec valeur commune aux variantes ; 111 avec valeurs/fourchettes conditionnelles supplémentaires. Montants de base, sans inventer les ajustements individuels de partage. |
| Blueprints | 692 références distinctes dans les pools, dont 662 reliées à un nom de produit. 324 descriptions et 697 candidates concernées. |
| Objets | 118 noms distincts, 162 descriptions ; quantités exactes ou fourchettes de variantes dans 139 descriptions. Destinataire propriétaire et livraison à la résidence indiqués uniquement quand les champs le précisent. |
| Variantes | 178 descriptions regroupent des variantes aux règles différentes. Une possibilité d'une variante ne devient pas un gain garanti pour toutes. |
| Nettoyage | 8 859 mentions de champs manquants supprimées par rapport au r4 ; 41 mentions de ce type conservées. Le comptage porte sur les lignes contenant `non communiqu`, `non confirm` ou `non détermin`, pas sur tous les avertissements utiles. |

Le mécanisme standard est conditionnel : partage de la mission, puis acceptation par les joueurs. La simple présence dans un groupe ne constitue pas un partage confirmé. Le pack ne divise lui-même aucun montant par un nombre de joueurs supposé. « Contrat non partageable » n'est pas présenté comme une preuve d'une exception propriétaire dans le moteur monétaire.

Pour les blueprints, le taux est celui du déclenchement du pool. Le nom d'un plan ne signifie pas une attribution garantie. Les poids du pool figurent dans les preuves ; ils ne deviennent pas un taux personnel définitif ignorant l'état du joueur. Aucun champ de bénéficiaire n'existe sur les résultats `BlueprintRewards` examinés : l'avertissement sur l'attribution à chaque équipier reste donc affiché.

Les points de scénario disposent de leur propre champ `splitPointsForParty`, exploité séparément des crédits. La réputation n'est jamais renommée XP. Aucune mécanique indépendante d'XP n'est corroborée : aucune ligne « XP non communiqué » n'est ajoutée.

## Sources réellement examinées

- [CIG — Missions and Contracts](https://support.robertsspaceindustries.com/hc/en-us/articles/360008918933-Missions-and-Contracts) : action de partage, acceptation des autres joueurs et partage égal des récompenses. Source générale actuelle, pas une mesure serveur du build.
- DataCore du build exact : [extraction Windows 45050504173](https://github.com/madoredylan01-debug/omnia-link/actions/runs/45050504173), 63 327 enregistrements inspectés, 11 171 retenus ; recherche des contrôles de distribution dans tous les enregistrements. Les trois correspondances explicites trouvées concernent la progression de scénario, pas un barème d'exception de partage des crédits.
- Références de réputation, factions, montants, paliers, bonus, conditions, récompenses, blueprints, produits et noms de localisation. Les tables de bonus non reliées à une mission ne lui sont pas attribuées par supposition. Un montant nul sans calculateur n'est plus décrit comme un paiement calculé.
- 465 modules de mission client non chiffrés : 3 877 891 octets décodés, intégrité ZIP/P4K vérifiée, aucune erreur de lecture CryXML. Parmi les 82 chemins de modules référencés par les brokers candidats, seuls deux sont présents dans ce sous-ensemble client. Les fonctions disponibles exposent notamment des variables et un plafonnement de récompense ; elles ne donnent pas une implémentation complète des versements serveur pour les 80 autres références.
- [StarCitizenWiki/API](https://github.com/StarCitizenWiki/API/blob/23082ea7dbd1f916939b971a6bdad4c04832f1ad/app/Jobs/Game/ImportMissionData.php), MIT : comparaison des champs de récompenses fixes/calculées, réputation, pools et objets. La [table publique](https://api.star-citizen.wiki/missions) étiquette « XP » son champ `reputation_amount` : cela ne prouve pas un système d'XP distinct. Aucune base tierce non vérifiée pour ce build n'est recopiée.
- [SuperCargo](https://github.com/AquatikJustice/SuperCargo/blob/665622d68eb97dde03946e2a19ab207b49fdad94/src/main/logParser.ts), MIT : lecture d'événements de partage, d'entrée/sortie et de récompense dans les journaux. Cette méthode requiert un état d'exécution du joueur ; elle n'est pas un champ calculable dans `global.ini`. Aucun suivi de journal n'est ajouté au PC.
- [Lazy Citizen](https://github.com/altibola/lazy-citizen-enhancements), Apache-2.0, générateur consulté : résolution UUID de pools et variantes, constat des récompenses dynamiques. Les données numériques d'un ancien build ne sont pas reprises.
- SC Market, RMTV et SCMDB consultés pour comparaison. Leurs regroupements, étiquettes « XP » et données sans preuve du build exact ne sont pas utilisés comme nouvelles valeurs de production.
- Le commentaire de support reproduit sur un miroir Issue Council pour le build 13165946 n'est pas utilisé comme preuve d'un versement exact en 13220821.

Le lecteur CryXML ajouté est une implémentation indépendante du format de tables documenté, avec contrôles de bornes, de parents, de chaînes et de cycles. Aucun code tiers sans licence n'est incorporé. Les modules bruts et le dump DataCore restent des entrées privées de recherche ; seuls les faits utiles et leur provenance sont publiés.

## Localisation et limites

Les 2 039 descriptions traitées sont conservées dans l'inventaire. 897 blocs sans information supplémentaire utile sont retirés ; 1 142 descriptions contiennent un bloc adapté, utilisé par 4 123 définitions dont 3 685 candidates. Ce changement de comptage ne correspond pas à une suppression du corps français.

Les 74 clés de description absentes, les huit emplacements partagés protégés et les 112 définitions sans description résolue restent documentés. La localisation globale reste partielle : 65 653 entrées françaises réutilisées/révisées, 10 616 noms officiels conservés, 15 089 entrées anglaises ou inchangées, sur 91 358 clés.

Une description statique ne connaît ni l'effectif ayant accepté le contrat, ni les versements, bonus ou états de progression calculés sur le serveur. Les variables natives déjà présentes sont préservées, sans en inventer pour un effectif ou un calcul. Les données de référence et variantes sont consultables dans les preuves du pack ; aucune interface complémentaire non développée n'est annoncée comme opérationnelle.

La compatibilité reste strictement limitée au build 13220821, recontrôlé dans le manifeste local. La page de statut CIG consultée annonce encore 13165946 ; elle ne sert pas à déclarer une compatibilité avec un autre build. Un nouveau build réclame ses propres références et une validation.

## Validation

50 tests JavaScript locaux réussis, dont le décodage de tables CryXML, les gardes contre les erreurs de conversion, les variantes, les quantités et la séparation des règles de partage. Les résultats Windows et le téléchargement du catalogue public sont consignés dans le reçu de validation après leur exécution.

À vérifier en jeu par le joueur : une mission partagée et acceptée (au moins deux joueurs), une mission non partageable, un contrat à blueprint, un contrat à quantité d'objets et une progression de scénario. Comparer offres et versements, vérifier les bénéficiaires, la substitution des variables, les fourchettes par variante et la lisibilité des descriptions. Aucune nouvelle observation de ces versements n'est prétendue. Le jeu n'est pas lancé et l'écran personnel n'est pas capturé.
