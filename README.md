# Planning des séances — Widget Grist

Widget personnalisé pour [Grist](https://www.getgrist.com/) permettant d'afficher des événements ou des séances sous forme de planning chronologique interactif.

Le widget est conçu pour être **réutilisable dans différents documents Grist**, à condition de disposer des colonnes attendues et d'adapter leur correspondance (*mapping*).

## Démonstration et utilisation

**URL du widget :**

https://lucgaudard.github.io/grist-widgets/planning.html

**Code source :** `planning.html`

Le widget est hébergé sur GitHub Pages.

## Fonctionnalités

- Affichage chronologique des événements, regroupés par jour.
- Navigation mensuelle et accès direct à la date du jour.
- Affichage des horaires, du titre et d'informations complémentaires.
- Couleurs personnalisées selon une catégorie.
- Badge indiquant le groupe ou une autre information courte.
- Indicateurs **R** (ressources) et **P** (prérequis), visibles uniquement lorsque les champs correspondants sont renseignés.
- Volet dépliable pour consulter les ressources et prérequis au format Markdown.
- Sélection d'un événement synchronisée avec les autres vues Grist liées.

## Installation

1. Ajouter une vue **Widget personnalisé** dans un document Grist.
2. Sélectionner la table contenant les événements.
3. Renseigner l'URL du widget.
4. Configurer les colonnes nécessaires au fonctionnement du planning.
5. Autoriser les accès requis par le widget.
6. Tester l'affichage et la synchronisation avec les autres vues.

Le widget peut être utilisé avec une table classique ou une table de synthèse (*Grouper par*), sous réserve que les colonnes nécessaires soient disponibles.

## Colonnes attendues

Les noms ci-dessous correspondent aux **identifiants techniques actuellement attendus par le code HTML**.

| Colonne technique | Utilisation |
|---|---|
| `Date_debut` | Date et heure de début |
| `Date_fin` | Date et heure de fin |
| `Libelle_calendrier` | Titre affiché sur la carte |
| `Groupe_sans_vague` | Badge affiché en haut à droite |
| `Ressources_associees` | Contenu Markdown des ressources |
| `Prerequis` | Contenu Markdown des prérequis |
| `Cours` | Référence utilisée pour déterminer la catégorie et la couleur |

Les champs de ressources et de prérequis peuvent rester vides. Les indicateurs correspondants sont alors masqués.

**Important :** le widget n'est pas encore équipé d'une interface permettant d'associer librement les colonnes Grist aux champs du planning. Le mapping dépend actuellement des identifiants utilisés dans le code.

Pour réutiliser le widget dans un autre document, il faut donc soit conserver les identifiants techniques attendus, soit adapter le code HTML.

## Couleurs des catégories

Le widget prend en charge des couleurs définies dans Grist.

Dans son implémentation actuelle, il exploite notamment les informations de catégorie provenant de la table `Cours`, et les couleurs configurées dans les options des choix de la colonne `CatCours`.

Cette partie suppose une structure de références compatible et peut nécessiter une adaptation dans un autre document.

## Gestion des accès

Le widget exploite les enregistrements transmis par la source de données configurée dans Grist.

Les autorisations d'accès et les restrictions de lecture doivent être définies dans les **règles ACL de Grist**.

Le widget ne constitue pas un mécanisme de sécurité autonome.

Lorsqu'une table de synthèse est utilisée, il convient de vérifier les règles d'accès de cette table et leur effet sur les données effectivement affichées.

## Maintenance

Le fichier `planning.html` constitue la version officielle du widget.

Les évolutions et versions précédentes sont conservées dans l'historique des commits GitHub.

Avant de publier une modification, vérifier :

- Le chargement des événements et leur ordre chronologique.
- Les dates, horaires, couleurs et badges.
- L'affichage conditionnel des indicateurs R et P.
- Le rendu Markdown des volets dépliables.
- La synchronisation des enregistrements avec Grist.
- Le respect des restrictions de lecture définies dans le document.

## Licence

Aucune licence de réutilisation n'est définie pour le moment.
