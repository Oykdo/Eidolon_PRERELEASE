# Architecture conceptuelle d'Eidolon

Ce document décrit l'architecture d'Eidolon au niveau conceptuel. Il ne contient **ni paramètres cryptographiques précis, ni détails d'implémentation, ni structures de fichiers internes**. Ces éléments sont volontairement réservés jusqu'à l'audit externe indépendant.

---

## Vue d'ensemble

Eidolon est un vault cryptographique local qui produit une identité souveraine à partir d'une **clé holographique** — un objet cryptographique composé de deux fragments complémentaires, ni l'un ni l'autre suffisant seul pour débloquer le coffre.

Le système s'articule autour de quatre sous-systèmes :

```
┌────────────────────────────────────────────────────────────┐
│                       Eidolon                              │
├────────────────────────────────────────────────────────────┤
│                                                            │
│   1. Pipeline cryptographique                              │
│   2. Identité et persistance du coffre                     │
│   3. Ressources holographiques                             │
│   4. Intégration blockchain                                │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

Chaque sous-système est conçu pour être **indépendamment vérifiable** et repose sur des primitives cryptographiques standardisées ou candidates à la standardisation.

---

## 1. Pipeline cryptographique

Le pipeline de génération produit une clé holographique à haute entropie effective. Le processus est déterministe relativement à ses entrées et produit des artefacts vérifiables.

### Propriétés garanties

| Propriété | Assurance |
|-----------|-----------|
| Résistance quantique | Primitives post-quantiques en sortie |
| Résistance aux canaux auxiliaires | Opérations en temps constant |
| Intégrité des fichiers | Authentification cryptographique par artefact |
| Protection des métadonnées | Masquage interne réversible |
| Non-falsifiabilité | Signatures post-quantiques |

Les primitives mises en œuvre sont issues de la cryptographie post-quantique en cours de standardisation et de techniques cryptographiques vérifiables éprouvées. **Les détails précis — familles d'algorithmes retenues, paramètres, ordre des étapes, transformations intermédiaires, sources d'entropie, tests de qualité — ne sont pas publiés à ce stade** et feront l'objet d'une divulgation progressive après l'audit externe.

---

## 2. Identité et persistance du coffre

### Authentification à deux fragments

L'accès à un coffre Eidolon requiert **deux fichiers distincts** :

- un fragment **cryptographique** contenant les matériaux de clé
- un fragment **structurel** contenant la représentation holographique

Aucun des deux fragments seul ne permet de débloquer le coffre, ni d'en reconstruire l'autre. Cette séparation permet par exemple de stocker les deux fragments sur deux supports physiques distincts, ou d'en confier un à un tiers de confiance sans risque.

### Identité dérivée

L'identifiant unique d'un coffre (`vault_id`) est dérivé cryptographiquement des deux fragments. Il ne peut être falsifié sans posséder les fragments originaux, et il est stable dans le temps tant que les fragments ne sont pas modifiés.

### Verrou machine

Un coffre est **lié à un dispositif** au moment de son enregistrement. Cette liaison est volontaire et assumée : elle empêche l'utilisation simultanée d'une même identité depuis plusieurs machines sans intention explicite de transfert.

Le transfert d'une identité vers une nouvelle machine passe par un processus explicite d'**attestation de révocation** sur l'ancienne machine, produisant un artefact vérifiable par la nouvelle.

### État local chiffré

Toutes les données d'état d'un coffre (balance, historique, actifs, métadonnées) sont stockées **localement, sous forme chiffrée**, dans un format fichier lisible ligne à ligne. Il n'existe aucune base de données centralisée.

Cette approche *file-based* offre plusieurs garanties :

- **Auditabilité** : l'état peut être inspecté sans infrastructure
- **Portabilité** : un coffre est une arborescence de fichiers transportable
- **Indépendance serveur** : aucun tiers ne détient votre état
- **Résilience** : pas de point de défaillance central

---

## 3. Ressources holographiques

### Avatar cryptographique

Chaque coffre possède un **avatar** — une représentation visuelle 3D générée déterministiquement à partir des données cryptographiques de la clé holographique. L'avatar n'est pas une image stockée : c'est une **projection vivante** de la clé, régénérable à tout moment depuis les fragments.

L'avatar est structuré en **couches holographiques** qui représentent différents aspects de l'identité du coffre :

- des couches structurelles toujours actives (forme, cœur, résonance)
- des couches ornementales (couronnes, halos, anneaux orbitaux)
- des couches de données cryptographiques activables (signature multi-vectorielle, corrélations quantiques, masque temporel)

Certaines couches évoluent dans le temps en fonction de l'**âge du coffre** — plus un coffre est ancien, plus sa signature visuelle intègre de dérivations temporelles.

### Économie runtime

Un coffre Eidolon possède une **économie interne** qui reflète sa vitalité opérationnelle. Cette économie n'est pas spéculative : elle fonctionne comme un système de **crédits d'utilisation** reflétant l'activité du coffre.

Les grandeurs suivies incluent :

- une **balance** d'unités Eidolon (monnaie opérationnelle runtime)
- un **score de résonance** reflétant la stabilité du coffre
- une mesure d'**entropie opérationnelle** accumulée par l'usage

Des mécanismes périodiques (*ticks*) appliquent des gains et des coûts de maintenance, garantissant que l'économie reste dynamique et liée à l'usage réel.

### Allocation fondateur (PSNX)

Parallèlement à la monnaie runtime, Eidolon réserve une **allocation fondateur** distincte (PSNX) avec un plafond fixe à 21 millions d'unités, inspiré du modèle Bitcoin. Cette allocation est distribuée selon des **paliers** basés sur l'ordre d'enregistrement des coffres :

- les premiers coffres reçoivent des allocations significatives avec vesting progressif
- les allocations décroissent par paliers successifs
- au-delà du 10 000e coffre, les nouveaux arrivants ne reçoivent pas d'allocation fondateur mais peuvent participer pleinement à l'économie runtime

Cette double économie sépare clairement **valeur opérationnelle** (runtime) et **prime d'antériorité** (allocation fondateur).

### Simulation physique

Certaines étapes du pipeline cryptographique utilisent une **simulation physique déterministe** de polyèdres dans un environnement paramétré. Cette simulation sert de source d'entropie vérifiable : deux exécutions avec les mêmes paramètres produisent le même résultat, mais la sensibilité aux conditions initiales garantit une diffusion cryptographique élevée.

Chaque polyèdre est instancié avec des propriétés matérielles sélectionnées déterministiquement dans un **catalogue de matériaux réels**, ajoutant une couche d'entropie dépendante du matériau qui rend toute tentative de force brute substantiellement plus coûteuse.

---

## 4. Intégration blockchain

Eidolon intègre une couche blockchain **optionnelle** qui permet à un coffre de posséder et gérer des actifs on-chain sans compromettre la souveraineté locale.

### Portefeuilles multi-chaînes

Le coffre peut dériver, à partir de sa clé racine, des **portefeuilles hiérarchiques déterministes** pour plusieurs blockchains EVM (Ethereum, Polygon, Arbitrum, Base) ainsi que Bitcoin. La dérivation est standard (BIP-32 / BIP-44) et les clés privées ne quittent jamais le coffre.

### Avatar inscrit

L'avatar cryptographique peut être **inscrit on-chain** sous forme d'Ordinals Bitcoin ou de NFT EVM. L'inscription n'est **pas** la clé — elle est une preuve publique d'existence de l'avatar à un instant donné, utile pour l'horodatage et la traçabilité.

### Principe de non-dépendance

La blockchain est utilisée comme **registre public optionnel**, jamais comme source de confiance. Un coffre Eidolon fonctionne intégralement **sans connexion blockchain**. L'intégration est additive, non constitutive.

---

## Flux de vie d'un coffre

```
  ┌─────────────┐
  │   Genèse    │  Génération des deux fragments + identité
  └──────┬──────┘
         │
  ┌──────▼──────┐
  │Enregistrement│ Liaison machine + attribution fondateur
  └──────┬──────┘
         │
  ┌──────▼──────┐
  │  Runtime    │  Économie, maintenance, avatar vivant
  └──────┬──────┘
         │
  ┌──────▼──────┐
  │  Transfert  │  Optionnel : révocation attestée + renaissance
  └─────────────┘
```

Chaque étape est cryptographiquement vérifiable par des artefacts produits en local, sans dépendance serveur.

---

## Galerie holographique

Les captures ci-dessous illustrent les **11 couches visuelles** du viewer holographique d'un coffre Eidolon. Chacune est une signature 3D déterministe dérivée des données cryptographiques de la clé — deux coffres identiques produisent le même visuel ; deux coffres différents en produisent des signatures strictement distinctes.

Ces enregistrements proviennent d'un **vaisseau de test synthétique** (données non-réelles, seeds fixes) et servent à montrer la géométrie animée de chaque couche sans révéler les paramètres qui les génèrent.

| Couche | Nom | Rôle visuel |
|--------|-----|-------------|
| L0 | [Origin Key](./assets/L0_origin_key.webm) | Anneau orbital des 7 polyèdres fondateurs |
| L1 | [Inner Ring](./assets/L1_inner_ring.webm) | Tore de résonance interne |
| L2 | [Depth Axes](./assets/L2_depth_axes.webm) | Axes de profondeur dimensionnels |
| L3 | [Core Bloom](./assets/L3_core_bloom.webm) | Cœur icosaédrique animé |
| L4 | [Outer Shell](./assets/L4_outer_shell.webm) | Enveloppe sphérique filaire |
| L5 | [Orbit Ring](./assets/L5_orbit_ring.webm) | Anneau orbital étendu |
| L6 | [Crown Array](./assets/L6_crown_array.webm) | Couronne cérémonielle à 7 pointes |
| L7 | [Ascendant Halo](./assets/L7_ascendant_halo.webm) | Halo de Fresnel ascendant |
| L8 | [Couronne des Éons](./assets/L8_couronne_des_eons.webm) | Dérivation temporelle de l'âge du coffre |

Les couches L0-L7 sont **toujours actives** ; leur niveau de détail dépend du rang du coffre. La couche L8, illustrée ci-dessus, est **activable à la demande** et s'appuie directement sur l'âge du coffre. D'autres couches activables existent dans le système mais ne sont pas publiées à ce stade.

> Les captures ne contiennent **aucun code exécutable**. Les algorithmes de rendu, les paramètres de simulation chaotique, les constantes de masquage temporel et la logique d'extraction des données cryptographiques restent confidentiels jusqu'à l'audit externe.

---

## Modèle de menace

### Attaques considérées

| Vecteur | Mitigation |
|---------|-----------|
| Force brute classique | Espace de clé effectif élevé |
| Algorithmes quantiques (Grover) | Tailles de clé dimensionnées en conséquence |
| Algorithmes quantiques (Shor) | Primitives post-quantiques en sortie |
| Canaux auxiliaires (timing) | Opérations à temps constant |
| Cold boot | Effacement mémoire contrôlé |
| Falsification de fichiers | HMAC sur chaque artefact |
| Vol d'un fragment | Dual-key requis, un fragment seul est inutile |
| Perte d'un fragment | Récupération Shamir K-of-N optionnelle |

### Hors périmètre actuel

- **Compromission complète de la machine** (malware avec accès root actif) — aucun système local ne peut s'en prémunir entièrement
- **Attaques physiques sur le matériel** — une intégration HSM optionnelle est prévue
- **Ingénierie sociale ciblant l'utilisateur** — relève de l'hygiène opérationnelle

### Audit externe

Un **audit externe formel** par un cabinet spécialisé en cryptographie appliquée est prévu avant toute ouverture du code crypto-critique. Les résultats de cet audit conditionneront la publication des paramètres précis et de l'implémentation.

---

## Eidolon Connect

Au-delà du coffre individuel, Eidolon expose une **couche d'authentification réutilisable** nommée *Eidolon Connect*. Son objectif : permettre à des applications tierces d'authentifier leurs utilisateurs par **possession d'un coffre Eidolon**, sans mot de passe, sans email, sans fournisseur d'identité externe.

Le flux conceptuel :

1. L'application tierce demande une preuve de possession à l'utilisateur
2. Le coffre Eidolon produit une preuve à divulgation nulle
3. L'application vérifie la preuve et associe une session à l'identifiant du coffre
4. Aucun secret n'est transmis, aucun compte n'est créé côté serveur tiers

La première application cliente d'Eidolon Connect sera **Cipher**, une messagerie chiffrée de bout en bout développée en parallèle.

---

## Conventions techniques

- **Local-first** : toute fonctionnalité fonctionne hors-ligne par défaut
- **File-based** : pas de base de données, tout état est un fichier lisible
- **Déterminisme** : mêmes entrées ⟹ mêmes sorties, à toutes les étapes
- **Fail-closed** : en cas de doute cryptographique, refus d'accès
- **Migration douce** : chaque format a une version, les anciens formats restent lisibles

---

## Limites de cette documentation

Ce document décrit **l'architecture conceptuelle** d'Eidolon. Il ne contient volontairement pas :

- les paramètres cryptographiques précis (tailles de clés, algorithmes de hachage spécifiques, paramètres de dérivation)
- les formats de fichiers détaillés
- les structures de données internes
- les algorithmes de simulation précis
- les catalogues de matériaux ou de polyèdres
- les paramètres d'économie runtime (taux, seuils, multiplicateurs)

Ces éléments seront publiés **progressivement après l'audit externe**, accompagnés de leurs démonstrations formelles.

---

*Ce document est susceptible d'évoluer. Toute version antérieure reste valide pour la version d'Eidolon qu'elle décrit.*
