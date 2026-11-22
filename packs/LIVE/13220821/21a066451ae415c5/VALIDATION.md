# LIVE 13220821 r6 — correction des descriptions partagées

## Cause corrigée

`global.ini` ne désigne pas nécessairement une offre unique : plusieurs contrats utilisent la même clé. `HaulCargo_AtoB_desc` est référencée par 334 variantes. Le r5 calculait le minimum et le maximum de leurs récompenses, puis affichait cette fourchette sur l'offre sélectionnée. Il faisait de même pour la réputation. Ces agrégations ne décrivent pas la sélection du joueur et sont retirées du rendu.

Le montant natif de l'offre reste la référence. Aucune valeur telle que les « 53k » signalés par le joueur n'est codée en dur pour remplacer la valeur native. Aucun nouvel identifiant de variable n'est inventé. Un montant n'est répété que si la clé possède déjà une variable native de paiement, avec son unité vérifiée.

## Règles appliquées à toutes les descriptions

- Aucun montant monétaire statique ajouté, même s'il est commun aux variantes : le fichier ne connaît pas l'état de l'offre sélectionnée ni ses ajustements serveur.
- Aucune fourchette de réputation entre variantes. Une valeur de base n'est montrée que si toutes les variantes candidates concordent, que la réputation est corroborée et que leurs contrats ne peuvent pas être partagés. Cela n'est pas présenté comme une preuve d'un gain individuel net.
- La faction n'est affichée que lorsqu'elle est commune aux variantes. Les indications monétaires et de réputation restent indépendantes.
- Les libellés de partage fondés seulement sur la règle générale CIG sont retirés. Aucune nouvelle mention « individuelle », « partagée » ou « non partagée » n'est inventée pour les remplacer. Les données de recherche restent dans les preuves, sans devenir une affirmation dans le jeu.
- Plans : intersection des références corroborées dans **chaque** variante utilisant le texte, pas union des possibilités de toutes les offres. Trois noms au maximum, un par ligne, puis nombre d'autres possibilités. Les noms français existants sont utilisés quand disponibles ; les noms propres et modèles de vaisseaux sont conservés. Aucune traduction de nom n'est inventée.
- « Plans possibles (tirage) » ne promet ni un plan précis ni une attribution à chaque équipier. Aucun plan n'est annoncé garanti sans preuve suffisante.
- Objets : noms communs aux variantes, quantités communes exactes uniquement, deux lignes au maximum. Les bénéficiaires et remises ne sont précisés que par leurs champs explicites.
- Le budget est de 600 caractères pour le corps du bloc. Les groupes sont conservés ou omis entiers pour ne pas couper une réserve de sens. Maximum observé du bloc complet : **462 caractères**, contre 1 562 dans le r5.
- Les anciens récapitulatifs génériques sont également retirés pour ce build ; le corps français d'origine et les valeurs natives restent intacts.

Pour la description Covalex commune citée, le bloc devient :

```text
OMNIA — DÉTAILS DU CONTRAT
Faction : Covalex
```

Les 178 descriptions signalées par le r5 comme regroupant des règles différentes ont été auditées, ainsi que les 2 039 descriptions traitées. Les faits complets par variante restent dans `mission-facts.json`. L'audit avant/après et ses limites sont fournis avec le pack.

## Encodage et rendu

Les sauts de ligne sont les séquences littérales `\n` déjà utilisées dans les descriptions natives de Star Citizen. Le caractère `•` existe également dans la référence anglaise exacte, notamment les fiches de revendication Adagio. Les tests vérifient UTF-8, BOM, encodage des puces, séparation des lignes sans création de lignes INI parasites, nombre de lignes et limites des listes.

**Ces contrôles ne constituent pas un essai visuel dans le mobiGlas.** Aucun lancement du jeu ni capture de l'écran du joueur n'est effectué. Le comportement visuel exact du nouveau bloc et des puces reste à vérifier dans le moteur du jeu, pas dans une imitation HTML ou WebView2.

## Vérifications de livraison

62 tests JavaScript locaux réussis. Le workflow Windows exerce les commandes natives existantes sur des dossiers temporaires : téléchargement du catalogue candidat puis public, installation, vérification des écritures, restauration et réinstallation. Les résultats sont consignés après leur exécution.

Le validateur compare les 91 358 valeurs au r5 immuable. Seuls les suffixes OMNIA attendus et les anciens récapitulatifs peuvent changer. Corps français, menus, traductions et compléments hors missions restent identiques. BOM UTF-8, clés, variables, SHA-256, sauvegardes et gestionnaire de mise à jour sont préservés. Aucun installateur, autre module ou fichier du jeu installé n'est modifié par les tests.

## Contrôle précis restant sur le PC du joueur

Après « Mettre à jour », puis un lancement normal du jeu :

1. Revoir l'offre Covalex « Recrue — Moyen transport de fret direct ». Le paiement natif reste affiché par le jeu ; le bloc n'affiche plus de fourchette d'aUEC ou de réputation et indique seulement la faction pour la clé commune.
2. Ouvrir une offre à plans : vérifier une puce et un nom par ligne, au maximum trois plans, l'indication des autres possibilités et l'absence de chevauchement ou de glyphe manquant.
3. Ouvrir des offres appartenant à plusieurs rangs utilisant un même texte : vérifier qu'aucune fourchette globale ou possibilité réservée à une autre variante n'est attribuée à la sélection.
4. Vérifier le défilement, la fin de description et la lisibilité avec le réglage d'interface utilisé par le joueur. Les versements effectifs et éventuelles règles de partage particulières restent à observer indépendamment, sans assertion nouvelle dans le pack.
