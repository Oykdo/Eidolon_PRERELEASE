<div align="center">

# Eidolon

**Vault cryptographique post-quantique à clé holographique**

*Identité souveraine locale · authentification sans mot de passe · pas de serveur, pas de compte, pas d'email de récupération*

[![License: CC BY-ND 4.0](https://img.shields.io/badge/license-CC%20BY--ND%204.0-lightgrey.svg)](./LICENSE)
[![Status](https://img.shields.io/badge/status-pre--audit-orange.svg)](#statut)
[![Post-Quantum](https://img.shields.io/badge/crypto-post--quantum-blueviolet.svg)](#garanties-cryptographiques)
[![No Telemetry](https://img.shields.io/badge/telemetry-none-success.svg)](#valeurs-de-conception)
[![No Token Sale](https://img.shields.io/badge/token--sale-none-success.svg)](#valeurs-de-conception)

🇬🇧 *[English version available](./README.md)*

</div>

---

## Qu'est-ce qu'Eidolon ?

Eidolon est un coffre cryptographique local conçu autour d'une idée simple :

> **La possession d'une clé doit suffire à prouver une identité** — sans serveur central, sans mot de passe, sans compte à récupérer.

La clé n'est pas un fichier unique. C'est un **objet holographique** composé de deux fragments complémentaires qui, combinés, produisent une identité vérifiable avec une entropie élevée et une résistance aux attaques quantiques.

Autour de cette clé, Eidolon fournit :

- une **authentification sans secret partagé** — prouver qui vous êtes sans révéler votre clé
- une **identité unique par appareil**, non-transférable sans intention explicite
- une **signature visuelle cryptographique** (avatar) dérivée directement de la structure mathématique de la clé
- une **économie runtime** qui reflète l'activité et la vitalité du coffre
- une **couche blockchain optionnelle** pour portefeuilles HD, ancrage de documents et avatars NFT — tous enracinés dans la même clé

---

## Le problème que nous résolvons

L'infrastructure d'identité actuelle fuit de partout :

- Les **mots de passe** sont oubliés, réutilisés, phishés ou fuités. L'utilisateur moyen en jongle avec des dizaines et n'en retient aucun.
- Les **gestionnaires de mots de passe** concentrent toute votre vie numérique derrière un seul mot de passe maître — un point de défaillance unique.
- Les **fournisseurs d'identité** ("Se connecter avec...") peuvent révoquer votre accès à tout moment et observer toute votre activité.
- Les **seed phrases** transforment votre identité en 12 mots griffonnés sur papier — irrécupérables si perdus, dangereux si trouvés.
- Les **tokens matériels** exigent la confiance envers un vendeur, l'accès physique à un objet spécifique, et ne peuvent être ni copiés ni sauvegardés.
- Les **ordinateurs quantiques**, une fois opérationnels, casseront rétroactivement la plupart de la cryptographie déployée aujourd'hui.

Eidolon propose un modèle orthogonal : **votre identité est un objet mathématique que vous possédez physiquement**, réparti entre deux fragments cryptographiques, résistant aux attaques quantiques, vérifiable localement, et jamais transmis à qui que ce soit — pas même pour s'authentifier.

---

## La métaphore holographique

Un hologramme physique encode une scène 3D sur toute la surface de la plaque photographique. Coupez la plaque en deux : chaque moitié contient encore la scène entière — mais avec moins de résolution et demandant la bonne illumination pour se révéler.

La clé d'Eidolon suit le même principe, mathématiquement :

- **l'information est distribuée**, non concentrée en un seul endroit
- **deux fragments complémentaires** sont requis pour reconstruire l'identité complète
- une **"illumination" spécifique** (le protocole cryptographique) est nécessaire pour en révéler le contenu
- **l'avatar visuel** n'est pas une image de la clé — il *est* la clé, rendue en trois dimensions

Cette distribution est ce qui rend la clé résiliente face à une compromission partielle, robuste face à l'observation, et mathématiquement assez riche pour servir de racine à un système de confiance.

---

## Principes fondateurs

| Principe | Conséquence |
|----------|-------------|
| **Local-first** | Aucun serveur ne détient votre clé ni votre identité |
| **Zero-knowledge** | Prouvez ce que vous savez sans le révéler |
| **Post-quantique** | Résistant aux algorithmes quantiques connus |
| **Dual-fragment** | Deux fichiers distincts sont requis pour débloquer un coffre |
| **Lié à la machine** | Une identité est rattachée à un appareil, par conception |
| **État fichier** | Pas de base de données — chaque octet d'état est inspectable |
| **Hors-ligne par défaut** | Les opérations principales ne requièrent pas de réseau |
| **Zéro télémétrie** | Eidolon ne "phone home" jamais |

---

## Ce qui distingue Eidolon

Eidolon n'est pas un concurrent des outils existants — il occupe un autre coin de l'espace de conception.

| Outil existant | Sa force | Ce qu'Eidolon fait différemment |
|----------------|----------|---------------------------------|
| **Gestionnaires de mots de passe** | Stocker les secrets que vous possédez | Vous n'avez aucun mot de passe à stocker — votre clé *est* votre identité |
| **FIDO2 / Passkeys** | Auth forte liée à un service | Identité souveraine indépendante de tout service |
| **Seed phrases** | Sauvegarde portable pour wallets crypto | Deux fichiers cryptographiques, pas 12 mots à mémoriser |
| **Tokens matériels** | Possession physique = authentification | N'importe quel appareil peut être votre coffre — aucune dépendance vendeur |
| **SSO / OAuth** | Connexion cross-service pratique | Aucun fournisseur ne peut vous révoquer ni vous observer |

Eidolon est **complémentaire** à la plupart de ces outils. Il ne cherche pas à les remplacer — il vise à devenir la couche racine *sous* les applications qui dépendent aujourd'hui de mots de passe, d'email de récupération ou de fournisseurs centralisés.

---

## Garanties cryptographiques

Sans divulguer l'implémentation interne, le vault garantit les propriétés suivantes :

| Propriété | Garantie |
|-----------|----------|
| **Résistance quantique** | La sortie cryptographique repose sur des primitives post-quantiques |
| **Résistance aux canaux auxiliaires** | Les opérations sensibles s'exécutent en temps constant |
| **Intégrité des fichiers** | Chaque artefact persisté est authentifié cryptographiquement |
| **Protection des métadonnées** | Les métadonnées non-sensibles sont masquées au repos |
| **Non-falsifiabilité** | Les signatures cryptographiques empêchent l'usurpation d'identité |
| **Récupération optionnelle** | Un partage K-parmi-N peut être activé à la création |
| **Génération déterministe** | Mêmes entrées ⟹ même clé, de façon vérifiable |

Le pipeline interne, les choix de paramètres, les familles d'algorithmes, les sources d'entropie et les tests de qualité **ne sont pas divulgués à ce stade** et seront publiés progressivement après un audit externe formel (voir [feuille de route](#feuille-de-route)).

---

## Architecture en un coup d'œil

Eidolon s'organise en quatre sous-systèmes complémentaires :

1. **Pipeline cryptographique** — génération de clé holographique et primitives centrales
2. **Identité et persistance du coffre** — enregistrement, liaison appareil, état chiffré local
3. **Ressources holographiques** — avatar cryptographique, économie runtime, signature visuelle
4. **Intégration blockchain** — portefeuilles HD multi-chaînes, inscriptions d'avatars

Voir [`ARCHITECTURE.md`](./ARCHITECTURE.md) pour la description conceptuelle de chaque sous-système, ainsi que la galerie animée du viewer holographique.

---

## Cas d'usage

Eidolon est conçu comme une **couche d'identité racine**. Il ne livre pas une application unique — il habilite une classe d'applications qui seraient maladroites ou impossibles avec l'infrastructure d'identité actuelle.

**Scénarios utilisateur final :**
- Se connecter à un service sans jamais créer de compte ni de mot de passe
- Signer un document de façon vérifiable hors-ligne, pour toujours, même face à un adversaire quantique
- Prouver que vous êtes la même personne à travers plusieurs services — sans lier ces services entre eux
- Gérer des portefeuilles de cryptomonnaie avec une racine de confiance unique partagée avec le reste de votre identité
- Échanger des messages chiffrés de bout en bout avec un contact dont vous avez vérifié le coffre une seule fois

**Scénarios développeur / intégrateur :**
- Remplacer le flux "email + mot de passe + récupération" par une connexion sans mot de passe basée sur le coffre
- Émettre des attestations cryptographiques que l'utilisateur contrôle, pas vous
- Ajouter une couche d'authentification post-quantique à un service existant sans réécrire toute sa logique d'auth
- Construire une application décentralisée où les utilisateurs possèdent leur identité sans dépendre d'une blockchain

Le **premier client réel** de ce modèle est **Cipher**, une messagerie chiffrée de bout en bout développée en parallèle, qui utilise Eidolon pour l'authentification sans mot de passe.

---

## Questions fréquentes

**Que se passe-t-il si je perds un des deux fragments ?**
Sans partage de récupération configuré à l'avance, la perte est définitive. C'est un choix de conception : la souveraineté implique la pleine responsabilité. Un partage K-parmi-N optionnel est disponible à la création pour les utilisateurs qui veulent un filet de sécurité.

**Puis-je transférer mon identité vers un nouvel ordinateur ?**
Oui, via un processus explicite de *révocation-renaissance*. Il n'y a aucun transfert silencieux — déplacer un coffre est un acte cryptographique intentionnel, vérifiable depuis les deux machines.

**Eidolon a-t-il besoin d'internet pour fonctionner ?**
Non. Génération de clé, authentification, signature et opérations du coffre fonctionnent entièrement hors-ligne. Le réseau n'est utilisé que lorsque vous le demandez explicitement (par exemple pour interagir avec une blockchain ou un service tiers).

**Mes données sont-elles envoyées quelque part ?**
Non. Eidolon ne "phone home" pas, ne collecte pas de télémétrie, et n'effectue ni "synchronisation d'arrière-plan" ni "sauvegarde cloud" sans action explicite de votre part. Votre coffre vit sur votre appareil, point.

**Pourquoi le code n'est-il pas encore open source ?**
Publier du code cryptographique avant un audit externe est irresponsable. Un attaquant peut étudier vos faiblesses plus vite qu'une communauté de volontaires ne peut les trouver et les signaler. Le projet s'engage sur un audit externe complet avant toute divulgation de code, suivi d'une ouverture progressive du noyau cryptographique.

**Y a-t-il une ICO, un token sale ou une pré-vente ?**
Non. Eidolon n'a pas de token de levée de fonds, pas d'ICO, et pas de pré-vente. Personne ne peut acheter son entrée dans le projet — PSNX ne peut être acquis contre de l'argent à aucun stade.

**Y a-t-il une allocation pour les premiers utilisateurs ?**
Oui, en toute transparence. Les **10 000 premiers coffres** enregistrés reçoivent une **allocation fondateur PSNX** selon un calendrier de vesting progressif, distribuée par paliers basés sur l'ordre d'inscription. L'offre totale de PSNX est **plafonnée à 21 millions d'unités**, fixe par conception (modèle Bitcoin, aucune émission future possible). Cette allocation récompense le fait d'*être précoce à l'écosystème*, pas une contribution financière — elle n'est ni vendue, ni cotée publiquement, ni présentée comme un véhicule spéculatif. Voir [`ARCHITECTURE.md`](./ARCHITECTURE.md#allocation-fondateur-psnx) pour la structure des paliers.

**Quand sera-t-il production-ready ?**
Quand la Phase 1 sera stabilisée et que le SDK de Phase 2 sera disponible. Aucune date fixée n'est communiquée — la qualité et la correction priment sur le calendrier.

**En quoi est-ce différent d'un portefeuille blockchain ?**
Un portefeuille blockchain détient des clés pour une chaîne spécifique. Eidolon détient une *identité* qui peut optionnellement piloter des portefeuilles sur n'importe quelle chaîne — et qui sert aussi à l'authentification, la signature, la messagerie, et plus. La blockchain est un cas d'usage aval, pas le but principal.

**Qui est derrière Eidolon ?**
Eidolon est actuellement développé en solo, en phase pré-communauté. Le projet évite volontairement de se précipiter dans des structures de communauté/gouvernance avant que le noyau cryptographique ne soit audité et stable.

---

## Valeurs de conception

| Valeur | En pratique |
|--------|-------------|
| **Audit avant open-source** | Le système fonctionnel et les docs viennent d'abord ; le code ne s'ouvre qu'après audit formel |
| **Pas de tokenisation prématurée** | Pas d'ICO, pas de pré-vente, pas de levée de fonds publique — PSNX est une allocation fondateur interne, pas un instrument financier |
| **Longévité plutôt que vitesse** | Conçu pour fonctionner encore dans 30 ans, pas pour gagner un hackathon |
| **Vos données vous appartiennent** | Pas de sauvegarde silencieuse, pas d'upload "de confort", pas d'analytics tiers |
| **Badges honnêtes** | Le README reflète l'état réel du projet, y compris ce qu'il n'est *pas* encore |
| **Souveraineté = responsabilité** | La récupération est opt-in, pas automatique |

---

## Statut

**Eidolon est en développement actif, pré-audit de sécurité externe.** Ce dépôt est une **vitrine publique** — documentation et matériel visuel uniquement. Le code source, les paramètres précis et les détails d'implémentation ne sont pas publiés à ce stade.

### Objectifs futurs

Le projet s'engage sur ces objectifs, sans engagement de calendrier :

- **Stabiliser le produit central** — identité du coffre, authentification, économie runtime, et cycle de vie complet du coffre, de la genèse au transfert
- **Livrer le SDK Eidolon Connect** — une couche d'authentification réutilisable que des applications tierces peuvent intégrer pour offrir à leurs utilisateurs une connexion sans mot de passe et post-quantique
- **Distribuer sur plusieurs plateformes** — application desktop, compagnon mobile, extension navigateur, intégrations backend headless
- **Ouvrir le protocole** — spécification formelle du format de coffre et du protocole d'authentification, audit de sécurité externe par un cabinet indépendant de cryptographie, et soumission aux organes de standardisation concernés

L'audit externe précède toute divulgation du code source du noyau cryptographique. Aucune ouverture de code n'a lieu avant cette étape.

---

## À propos de ce dépôt

**Ce que contient ce dépôt :**
- La vision du projet et l'architecture conceptuelle (`README.md`, `ARCHITECTURE.md`)
- Une galerie animée des couches visuelles de l'avatar holographique (`assets/*.webm`)
- La licence régissant l'usage de cette documentation (`LICENSE`)

**Ce qui n'est PAS dans ce dépôt :**
- Le code source du pipeline cryptographique
- Les familles d'algorithmes exactes, paramètres, ou vecteurs de test
- Les spécifications de format de fichier
- La liste des primitives utilisées, leur ordre d'application, leur tuning
- Le catalogue matériaux, les choix de polyèdres, les constantes d'économie
- Toute suite de tests ou documentation interne

Ces éléments seront **divulgués progressivement après l'audit externe**, accompagnés de la spécification formelle du protocole.

---

## Contact

Pour toute demande sérieuse — partenariat, audit, intégration, collaboration recherche — **ouvrez une issue publique** en décrivant le contexte. Les demandes d'accès au code source seront évaluées au cas par cas.

Ce dépôt n'accepte pas de pull requests à ce stade, puisqu'il n'y a pas de code source à modifier.

---

## Licence

Ce dépôt — documentation, descriptions et matériel visuel — est publié sous [**CC BY-ND 4.0**](./LICENSE) (attribution obligatoire, pas de dérivés).

Le système Eidolon lui-même — code source, algorithmes, spécifications, implémentations — reste **propriétaire, tous droits réservés**. Aucune licence sur le code n'est accordée par la publication de cette vitrine.

---

<div align="center">

*Eidolon — votre identité, votre clé, votre souveraineté.*

</div>
