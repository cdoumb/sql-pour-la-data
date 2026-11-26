# Chapitre 1 — Pourquoi les bases de données, et pourquoi SQL ?

> **Objectifs de ce chapitre**
> - Comprendre à quoi sert une base de données.
> - Savoir ce qu'est SQL et d'où il vient.
> - Voir pourquoi c'est une compétence qui dure, en data comme en IA.

---

## 1.1 Un envoi d'argent, vu de l'intérieur

Tu envoies 5 000 FCFA à un ami depuis ton téléphone. Quelques secondes plus tard, ton solde baisse, le sien augmente, vous recevez chacun un SMS de confirmation, et l'opérateur garde une trace de l'opération.

Où sont enregistrées toutes ces informations ? Dans une **base de données**.

Maintenant, imagine ceci :

- des milliers de personnes envoient de l'argent **au même moment** ;
- le réseau coupe **au milieu** d'une opération ;
- un client conteste un transfert **six mois plus tard**.

Il faut que les soldes restent justes, que rien ne se perde et que l'on puisse retrouver n'importe quelle opération en un instant. C'est exactement le rôle d'une base de données.

## 1.2 Pourquoi pas un tableur ou des fichiers ?

Un tableur est excellent pour de petits calculs, mais il atteint vite ses limites.

| Besoin | Tableur / fichiers | Base de données |
|---|---|---|
| **Volume** | Environ un million de lignes par feuille, et la lenteur arrive bien avant | Conçue pour des millions, voire des milliards de lignes |
| **Utilisateurs simultanés** | Modifications qui s'écrasent | Accès concurrents gérés proprement |
| **Cohérence** | Rien n'empêche une erreur de saisie | Règles et contraintes appliquées automatiquement |
| **Sécurité** | Tout ou rien | Droits précis par utilisateur |
| **Retrouver une information** | Recherche manuelle | Requête précise en un instant |

## 1.3 Une base de données en trois idées

1. **Des tables.** Une table est un tableau : chaque colonne décrit une caractéristique, chaque ligne représente un élément.
2. **Des relations.** Les tables sont reliées entre elles par des identifiants (les *clés*), pour éviter de répéter les mêmes informations.
3. **Un SGBD.** Le *système de gestion de bases de données* (PostgreSQL, MySQL, SQLite…) est le logiciel qui stocke les données et répond à tes questions.

Exemple avec deux petites tables :

**clients**

| id_client | nom |
|---|---|
| 1 | Awa |
| 2 | Moussa |

**transactions**

| id_transaction | id_client | montant | date |
|---|---|---|---|
| 101 | 1 | 5000 | 2026-11-02 |
| 102 | 2 | 20000 | 2026-11-03 |
| 103 | 1 | 12500 | 2026-11-05 |

Le nom d'Awa n'est écrit qu'une seule fois : les transactions renvoient à elle grâce à `id_client`. Si elle change de nom, on corrige à un seul endroit.

## 1.4 SQL : poser des questions aux données

**SQL** (*Structured Query Language*) est le langage qui permet de dialoguer avec une base de données. Il est né dans les années 1970, avec les premiers systèmes relationnels, et il est normalisé depuis la fin des années 1980.

Sa grande force : il est **déclaratif**. Tu décris *ce que tu veux*, pas *comment l'obtenir*. Le SGBD se charge de trouver le meilleur chemin.

```sql
-- Quelles transactions dépassent 10 000 FCFA ?
SELECT id_transaction, montant
FROM transactions
WHERE montant > 10000;
```

Résultat :

| id_transaction | montant |
|---|---|
| 102 | 20000 |
| 103 | 12500 |

Quatre mots, et la question est posée. Il existe de petites différences d'un SGBD à l'autre (les *dialectes*), mais les fondations restent les mêmes. Ce que tu apprends ici te servira partout.

## 1.5 Pourquoi SQL reste incontournable

- **Il est partout.** Applications, banques, télécoms, e-commerce, administrations : la plupart stockent leurs données dans des bases interrogées en SQL.
- **Il dure.** Les outils à la mode changent vite. SQL, lui, a survécu à plusieurs décennies de nouveautés, et les outils récents (entrepôts de données dans le cloud, DuckDB, dbt, Spark SQL…) reprennent son langage ou s'en inspirent.
- **Il ouvre plusieurs métiers.** Analyste de données, data scientist, data engineer, ML engineer : tous ont besoin de lire et d'écrire des requêtes.
- **Il est au cœur de l'IA.** Un modèle n'est bon que si ses données le sont. Extraire, nettoyer, assembler les données et construire les variables d'entraînement passe très souvent par SQL. Les assistants IA savent générer des requêtes, mais il faut quelqu'un qui sache les **comprendre, les vérifier et les corriger**. Cette personne, ce sera toi.
- **Il rapporte vite.** Quelques semaines de pratique sérieuse suffisent pour devenir autonome sur de vraies analyses.

<!-- TODO : appuyer ces arguments par 2 ou 3 sources récentes (enquête développeurs, offres d'emploi data) avant publication. -->

## 1.6 Ce que tu sauras faire à la fin du livre

- interroger une base : filtrer, trier, regrouper, calculer ;
- relier plusieurs tables avec les jointures ;
- écrire des requêtes avancées (sous-requêtes, CTE, fonctions de fenêtrage) ;
- concevoir un schéma de base de données propre ;
- accélérer une requête lente ;
- préparer des données pour un projet d'analyse ou de machine learning.

## 1.7 Comment utiliser ce livre

1. **Installe l'environnement** (chapitre 2) : tu auras ta propre base en moins d'une heure.
2. **Tape chaque requête** au lieu de la copier.
3. **Casse-la et corrige-la** : on apprend beaucoup des messages d'erreur.
4. **Fais les exercices** avant de consulter les corrigés.

## À retenir

- Une base de données stocke des informations de façon **fiable, partagée et rapide à interroger**.
- Les données sont rangées dans des **tables reliées par des clés**.
- **SQL** est le langage pour poser des questions à ces données : il est stable, universel et central en data et en IA.
- Tu apprends en pratiquant : on commence au chapitre suivant.

## Pour aller plus loin

- Alan Beaulieu, *Learning SQL*, O'Reilly Media.
- Chaîne YouTube *Data with Baraa* (cours SQL gratuits).

  **Prochain chapitre : installer son environnement et écrire ses premières requêtes.**
