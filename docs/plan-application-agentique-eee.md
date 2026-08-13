# Plan de développement — application agentique pour un bureau d’experts en évaluation d’entreprises

**Version :** v1.0 — août 2026
**Auteur :** Philippe Prévost, Founding Partner, 1+1 Stratégie
**Statut :** plan de développement soumis pour arbitrage
**Portée :** conception, construction et déploiement d’une application agentique au service d’un bureau d’EEE (experts en évaluation d’entreprises), calibrée sur les normes de pratique en vigueur depuis le 1er janvier 2026.

---

## Sommaire exécutif

Un rapport d’évaluation de calibre mondial ne se distingue pas par sa longueur : il se distingue par sa **défendabilité**. Chaque chiffre remonte à une source, chaque hypothèse s’explique, chaque jugement professionnel se documente, et l’ensemble résiste au contre-interrogatoire. C’est précisément là que se situe l’occasion : la part du mandat qui consacre du temps à la collecte, à la normalisation, à la corroboration et à la traçabilité est massive, répétitive et faiblement créatrice de valeur — et elle est aujourd’hui outillable.

**Thèse du plan.** L’application ne rend pas de conclusion de valeur. Elle construit le dossier qui permet à l’EEE d’en rendre une plus vite, mieux étayée et intégralement traçable. L’agent est un analyste junior — jamais le signataire.

**Trois conditions de succès, non négociables :**

1. **La traçabilité précède l’automatisation.** La norme de documentation (PS 130) et l’obligation d’informer le tribunal du déroulement des travaux (art. 235 C.p.c.) imposent de pouvoir reconstituer qui a fait quoi, avec quelle source, à quel moment. Un journal d’audit exhaustif est le premier livrable, pas le dernier.
2. **Le jugement professionnel reste hors du périmètre.** Choix de l’approche, taux, primes et escomptes, appréciation du caractère raisonnable : l’agent prépare et documente, l’EEE tranche et signe.
3. **La conformité à la Loi 25 conditionne l’architecture.** Le traitement de données financières confidentielles hors Québec exige une évaluation des facteurs relatifs à la vie privée avant la première ligne de code d’intégration.

**Horizon :** cinq phases sur environ 30 à 40 semaines-personnes, chacune livrant une valeur autonome. Aucune phase ne dépend de la suivante pour être utile.

---

# Partie A — Le socle à outiller : ce que maîtrise un EEE senior

Cette partie répond à la question de fond — quelle formation, quelles règles et quelles capacités un EEE senior mobilise pour produire un rapport de calibre mondial. Elle sert de cahier des charges à la partie B : on n’outille bien que ce qu’on a d’abord cartographié.

## A.1 — Formation et accréditation

| Étape | Contenu |
|---|---|
| Préalable | Diplôme universitaire, le plus souvent doublé d’un titre de CPA ou de CFA |
| Programme d’études | Quatre cours obligatoires et deux cours à option parmi trois, à distance, offerts sur trois trimestres par année, chacun sanctionné par un examen. Durée usuelle : deux à trois ans |
| Examen de qualification des membres | Épreuve de quatre heures, une fois l’an en septembre, fondée sur des études de cas — évalue l’application des compétences en situation réelle, non la restitution théorique |
| Expérience | Minimum de 1 500 heures d’expérience pertinente en évaluation d’entreprises |
| Maintien | Formation continue et respect du code de déontologie de l’Institut |

**Lecture pour le plan :** la certification valide l’application du jugement en contexte, pas la mécanique de calcul. L’outillage doit donc viser la mécanique — et laisser intact ce qui est certifié.

## A.2 — Le cadre normatif en vigueur depuis le 1er janvier 2026

L’Institut a refondu ses normes de pratique au terme d’un processus pluriannuel comptant trois périodes de consultation. Les normes révisées s’appliquent aux mandats d’évaluation indépendante commencés à compter du 1er janvier 2026 — première refonte majeure depuis 2009-2010.

| Norme | Objet | Exigences structurantes |
|---|---|---|
| **PS 100** (nouvelle) | Concepts fondamentaux applicables à toutes les conclusions de valeur et à tous les rapports d’évaluation | Établit un cadre fondé sur des principes pour les trois niveaux de conclusion. Pose cinq principes cardinaux : **indépendance, objectivité, scepticisme professionnel, compétence en évaluation d’entreprises et jugement professionnel éclairé**. Consacre la responsabilité du professionnel de mener une étendue des travaux calibrée sur la finalité et les utilisateurs visés |
| **PS 110** | Divulgation dans le rapport | Étendue des travaux, information utilisée, jugements professionnels exercés, intrants et hypothèses significatifs, fondement des conclusions. Divulgation normalisée pour les conclusions de type Calcul et Estimation. Divulgation explicite des quatre conditions applicables aux rapports préliminaires |
| **PS 120** | Étendue des travaux | Revue, demandes d’information, analyse et **corroboration indépendante** de l’information significative sur l’entreprise, son secteur et les autres facteurs pertinents. S’applique désormais aux trois types de conclusions. Appréciation du caractère raisonnable global avant émission. Processus de contrôle qualité |
| **PS 130** | Documentation | Documentation des procédures d’indépendance et de vérification des conflits, y compris les facteurs considérés pour le mandat précis. Preuve documentaire de l’exécution du contrôle qualité exigé par la PS 120 |

**Trois déplacements de fond, décisifs pour la conception de l’application :**

- **Du rapport vers la conclusion.** Le centre de gravité passe du « rapport d’évaluation » à la « conclusion de valeur ». Les exigences d’étendue des travaux ne se modulent plus selon l’étiquette du rapport : elles s’appliquent aux conclusions Exhaustive, Estimation et Calcul.
- **L’adéquation à la finalité.** Le contenu et le niveau de détail se calibrent sur la finalité du mandat et les besoins des utilisateurs visés, non sur un gabarit uniforme.
- **La corroboration indépendante devient l’axe de gradation.** La PS 100 redéfinit les trois niveaux de conclusion en les distinguant par la profondeur de l’étendue des travaux — et plus précisément par **l’ampleur de la corroboration indépendante**. C’est le changement le plus lourd de conséquences pour l’outillage : ce qui sépare un Calcul d’une conclusion Exhaustive n’est plus une convention de présentation, mais une quantité de travail de recoupement mesurable.

La PS 100 définit le rapport d’évaluation comme « toute communication écrite contenant une conclusion quant à la valeur d’actions, d’actifs, de passifs ou d’une participation dans une entreprise, préparée par un évaluateur agissant de manière indépendante et objective »<sup>†</sup>. La définition est large : une note, un courriel chiffré ou une annexe de modèle peuvent y tomber. Le dispositif doit donc traiter toute sortie chiffrée comme potentiellement assujettie, et non seulement le document intitulé « rapport ».

<sup>†</sup> Traduction de travail. Le libellé officiel français doit être repris du texte de l’Institut avant toute citation externe.

**Compléments applicables :** les bulletins de pratique de l’Institut — dont le bulletin no 1 sur les rapports de critique restreinte et le bulletin no 3, qui porte des directives d’application. Depuis le 19 septembre 2023, les normes internationales d’évaluation (IVS) sont adoptées **en option**, aux côtés des normes de l’Institut; leur emploi n’est pas obligatoire.

## A.3 — Les obligations propres au contexte de litige au Québec

Dès qu’un rapport est destiné à un tribunal, un second cadre se superpose au cadre professionnel.

| Disposition | Contenu | Conséquence pour l’outillage |
|---|---|---|
| **Art. 22 C.p.c.** | L’expert a pour mission d’éclairer le tribunal; cette mission **prime les intérêts des parties**. Il l’accomplit avec objectivité, impartialité et rigueur | Aucun agent ne doit pouvoir être orienté vers un résultat souhaité. Les invites et les gabarits doivent être neutres par construction |
| **Art. 231 C.p.c.** | L’expertise vise à éclairer le tribunal en faisant appel à une personne compétente dans la matière concernée | La compétence est personnelle et non délégable à un système |
| **Art. 235 C.p.c.** | L’expert est tenu, sur demande, d’informer le tribunal et les parties de ses compétences, **du déroulement de ses travaux** et **des instructions reçues d’une partie** | Exigence la plus contraignante du plan : le déroulement des travaux doit être reconstituable intégralement, y compris la part assumée par des agents |

L’article 235 est le pivot. Un pipeline agentique dont on ne peut pas retracer le déroulement expose l’EEE à une attaque directe sur la recevabilité de son opinion. C’est ce qui justifie de construire le journal d’audit **avant** les agents.

## A.4 — La chaîne de valeur d’un mandat

| # | Étape | Nature dominante |
|---|---|---|
| 1 | Cadrage : finalité, utilisateurs visés, date d’évaluation, prémisse de valeur | Jugement |
| 2 | Indépendance et vérification des conflits | Procédure documentée |
| 3 | Collecte documentaire et contrôle de complétude | Procédure |
| 4 | Compréhension de l’entreprise et de son secteur | Analyse |
| 5 | Normalisation financière : retraitements, éléments hors exploitation, rémunération du propriétaire-dirigeant | Analyse et jugement |
| 6 | Choix des approches et méthodes | Jugement |
| 7 | Recherche de données de marché, de transactions et de multiples; corroboration indépendante | Procédure et analyse |
| 8 | Modélisation : actualisation des flux, capitalisation, actif net redressé; taux, primes et escomptes | Analyse et jugement |
| 9 | Appréciation du caractère raisonnable global | Jugement |
| 10 | Contrôle qualité et revue indépendante | Procédure et jugement |
| 11 | Rédaction et divulgation conformes | Procédure et rédaction |
| 12 | Défense : interrogatoire, contre-expertise, critique | Jugement |

Les étapes 3, 7, 10 et 11 concentrent l’essentiel des heures à faible valeur ajoutée. Ce sont les cibles prioritaires.

## A.5 — Les cinq marqueurs d’un rapport de calibre mondial

1. **Traçabilité intégrale.** Tout chiffre remonte à une source datée et archivée.
2. **Corroboration indépendante.** L’information significative fournie par le client est recoupée, pas reprise telle quelle.
3. **Explicitation du jugement.** Les hypothèses ne sont pas seulement énoncées : leur fondement est exposé, y compris les avenues écartées.
4. **Adéquation à la finalité.** Le niveau de détail correspond à l’usage et aux utilisateurs visés.
5. **Résistance à la critique adverse.** Le rapport a été lu, avant émission, par quelqu’un dont le mandat était de le démolir.

---

# Partie B — Traduction en architecture agentique

## B.1 — Principe directeur

L’adoption est déjà un fait dans la profession : au congrès de l’Institut de juin 2025, 87 % des répondants déclaraient utiliser des outils d’IA — 79 % pour la recherche, 55 % pour la rédaction de rapports, 23 % pour l’analyse. L’Institut n’a pas encore publié de lignes directrices propres à l’IA; son primer de juin 2024 pose le principe cardinal : l’IA sert à distiller l’information, appuyer la recherche et faciliter l’analyse — elle ne se substitue pas au jugement professionnel. La pratique dominante dans les grands cabinets traite l’agent comme un analyste junior : productif, encadré, systématiquement revu.

**Règle d’architecture retenue :** tout ce qu’un stagiaire de première année ferait sous supervision est automatisable. Tout ce qui exige la signature d’un EEE ne l’est pas.

## B.2 — Cartographie tâche → mode d’intervention

| Étape | Mode | Norme rattachée |
|---|---|---|
| Cadrage, finalité, prémisse de valeur | **Humain exclusif** | PS 100 |
| Vérification des conflits et documentation de l’indépendance | **Copilote** — l’agent recense et rédige, l’EEE atteste | PS 130 |
| Liste de documents, relances, contrôle de complétude | **Automatisé** | PS 120 |
| Compréhension du secteur, revue de presse, affichages de postes | **Automatisé**, sortie revue | PS 120 |
| Retraitements de normalisation | **Copilote** — l’agent propose et justifie, l’EEE retient | PS 120 |
| Choix des approches et méthodes | **Humain exclusif** | PS 100, PS 120 |
| Recherche de comparables et de multiples | **Copilote** avec corroboration obligatoire | PS 120 |
| Taux d’actualisation, primes, escomptes | **Humain exclusif**, calculs assistés | PS 120 |
| Appréciation du caractère raisonnable | **Humain exclusif** | PS 120 |
| Contrôle qualité et critique adverse | **Copilote** — l’agent produit la liste des faiblesses, l’humain arbitre | PS 120, PS 130 |
| Rédaction des sections descriptives et de divulgation | **Automatisé**, révision intégrale | PS 110 |
| Rédaction des sections de conclusion | **Copilote** sous dictée de l’EEE | PS 110 |
| Constitution du dossier de travail et journal d’audit | **Automatisé** | PS 130 |

## B.3 — Les huit agents

| Agent | Mission | Sorties |
|---|---|---|
| **Cadrage et conflits** | Structure la lettre de mission : finalité, utilisateurs visés, date, prémisse, type de conclusion. Balaie les parties liées contre le registre des mandats | Fiche de mandat, note d’indépendance à attester |
| **Collecte et complétude** | Génère la liste de documents adaptée au type de conclusion, suit les réceptions, signale les manques et leur incidence sur l’étendue des travaux | Tableau de complétude, projet de relance |
| **Normalisation financière** | Repère les éléments non récurrents, hors exploitation et de rémunération du propriétaire-dirigeant; propose chaque retraitement avec sa justification et sa source | Tableau de normalisation, BAIIA normalisé, journal des retraitements |
| **Recherche et corroboration** | Documente le secteur, les transactions comparables et les multiples; recoupe l’information client contre des sources externes datées. **Paramétré par niveau de conclusion** : la profondeur de recoupement exigée découle du niveau retenu au cadrage | Dossier sectoriel, tableau de comparables avec provenance, registre de corroboration |
| **Modélisation** | Monte les scénarios, exécute les tests de cohérence et de sensibilité, signale les écarts entre méthodes | Modèle, tableau de sensibilité, liste des incohérences |
| **Rédaction** | Produit les sections selon un gabarit conforme à la PS 110, dans la norme rédactionnelle fr-CA de la firme | Projet de rapport, tableau de couverture des divulgations |
| **Contrôle qualité et critique adverse** | Relit en posture de contre-expertise : affirmations non étayées, sauts logiques, divulgations manquantes, angles d’attaque probables | Liste de faiblesses classées par gravité |
| **Dossier de travail** | Consigne chaque intervention, source, version et validation humaine; constitue le dossier archivable | Journal d’audit, dossier de travail conforme PS 130 |

**Séquencement.** Les agents 2, 4 et 6 fonctionnent en pipeline sur un mandat donné. Les agents 3 et 5 exigent une validation humaine avant de transmettre leur sortie en aval. L’agent 7 s’exécute obligatoirement avant toute émission, y compris préliminaire. L’agent 8 est transversal et ne peut pas être désactivé.

## B.4 — Socle technique

| Couche | Fonction | Exigence |
|---|---|---|
| Ingestion | États financiers, déclarations, contrats, procès-verbaux, listes de prix | Extraction avec conservation de la référence page et de la version du document source |
| Base de dossier | Un espace cloisonné par mandat | Cloisonnement strict : aucun agent ne voit deux mandats à la fois |
| Recherche documentaire | Interrogation du dossier et des sources externes | Toute réponse porte sa citation; l’absence de source vaut refus de répondre |
| Bibliothèque de gabarits | Rapports, lettres de mission, listes de vérification par type de conclusion | Versionnée, avec date d’effet normative |
| Journal d’audit | Trace de chaque appel, invite, source, sortie et validation humaine | Immuable, exportable, lisible par un tiers |
| Garde-fous | Interdictions dures | Aucune conclusion de valeur générée; aucune émission sans passage de l’agent 7; aucune donnée client hors du périmètre autorisé |

## B.5 — Les cinq principes de la PS 100, traduits en contraintes de conception

| Principe | Traduction dans l’application | Ce qui reste hors machine |
|---|---|---|
| **Indépendance** | L’agent 1 balaie les parties liées et constitue la documentation exigée par la PS 130 | L’attestation d’indépendance, qui est personnelle |
| **Objectivité** | Invites et gabarits neutres par construction; aucun paramètre permettant d’orienter vers une fourchette souhaitée; toute instruction du client est horodatée au journal | L’arbitrage en cas de pression du mandant |
| **Scepticisme professionnel** | L’agent 7 opère en posture de contre-expertise; l’agent 4 signale les données client non recoupées | Le doute exercé sur une donnée qui « sent mauvais » sans anomalie formelle |
| **Compétence** | Le dispositif ne crée pas de compétence : il l’applique à l’échelle. L’accès aux agents suppose un EEE responsable du mandat | La compétence elle-même, personnelle et non délégable (art. 231 C.p.c.) |
| **Jugement professionnel éclairé** | L’agent fournit la matière du jugement — options, sources, écarts, sensibilités | Le jugement, en totalité |

Le registre de corroboration mérite une mention distincte. Puisque le niveau de conclusion se distingue désormais par l’ampleur du recoupement indépendant, ce registre devient la pièce qui démontre que le niveau annoncé a bien été atteint. Il doit répondre à une question simple, poste par poste : cette donnée a-t-elle été recoupée, contre quoi, et sinon, pourquoi.

## B.6 — Le journal d’audit, pièce maîtresse

Le journal n’est pas une commodité d’ingénierie : c’est le livrable qui rend l’ensemble défendable. Il doit permettre de répondre, sous serment, à trois questions :

- Quelle information a servi à cette conclusion, et d’où provenait-elle ?
- Quelle part du travail a été exécutée par un agent, et qui l’a validée ?
- Quelles instructions ont été reçues du client, et à quel moment ont-elles influencé les travaux ?

Un journal qui ne répond pas à ces trois questions ne satisfait ni la PS 130 ni l’article 235 C.p.c.

---

# Partie C — Conformité et gestion du risque

| Domaine | Obligation | Incidence sur le plan |
|---|---|---|
| **Loi 25 — transfert hors Québec** | Depuis septembre 2023, toute communication de renseignements personnels hors Québec exige une évaluation des facteurs relatifs à la vie privée (EFVP) établissant une protection adéquate | Détermine le choix d’hébergement et de fournisseur de modèles. À trancher en phase 0, avant toute intégration |
| **Loi 25 — décision automatisée** | Évaluation d’impact exigée pour les systèmes de décision automatisée; transparence sur les algorithmes; droit à des explications | L’architecture retenue — aucune décision rendue par un agent — réduit l’exposition, sans l’annuler. À documenter explicitement |
| **Loi 25 — sanctions** | Jusqu’à 25 M$ ou 4 % du chiffre d’affaires mondial | Justifie de traiter la conformité comme condition préalable, non comme chantier parallèle |
| **Secret professionnel et confidentialité** | Données financières et personnelles de tiers dans chaque dossier | Cloisonnement par mandat; aucun entraînement de modèle sur les données de dossier; clauses contractuelles avec les fournisseurs |
| **Divulgation de l’usage de l’IA** | La pratique émergente veut que le degré de divulgation soit proportionnel à l’importance de l’usage : résumer des rapports sectoriels n’équivaut pas à bâtir un modèle central | Établir une politique de divulgation par palier et l’inscrire au gabarit de rapport |
| **Indépendance** | La PS 130 exige la documentation des procédures d’indépendance et de conflits | L’agent 1 produit la documentation; l’attestation reste personnelle |
| **Responsabilité professionnelle** | L’assureur doit connaître le dispositif | Aviser l’assureur avant le déploiement en production, pas après |
| **Lettres de mission** | Encadrer contractuellement l’usage d’outils assistés | Réviser les gabarits en phase 0 |

---

# Partie D — Feuille de route

Les efforts sont exprimés en semaines-personnes et constituent des ordres de grandeur à calibrer sur la taille du bureau.

### Phase 0 — Cadrage et conformité (2 à 3 semaines)

- Inventaire des types de mandats et de leur volume; choix des deux cas d’usage pilotes
- EFVP et arbitrage d’hébergement; sélection du fournisseur de modèles
- Révision des gabarits de lettre de mission; politique de divulgation par palier
- Avis à l’assureur en responsabilité professionnelle

**Critère de sortie :** décision d’hébergement signée et EFVP consignée. Sans cela, rien ne démarre.

### Phase 1 — Socle documentaire et traçabilité (4 à 6 semaines)

- Base de dossier cloisonnée, ingestion avec référence à la source
- Journal d’audit immuable et exportable
- Bibliothèque de gabarits versionnée, alignée sur les normes en vigueur depuis le 1er janvier 2026

**Critère de sortie :** on peut reconstituer intégralement le déroulement d’un mandat test. **Valeur autonome :** même sans agent, le bureau y gagne un dossier de travail conforme.

### Phase 2 — Agents à faible risque (6 à 8 semaines)

- Agents Collecte et complétude, Recherche et corroboration, Dossier de travail
- Mesure de l’écart entre la sortie de l’agent et le travail humain sur cinq mandats témoins

**Critère de sortie :** réduction mesurée des heures de collecte et de recherche, à qualité de dossier constante.

### Phase 3 — Rédaction et contrôle qualité (6 à 8 semaines)

- Agent Rédaction sur les sections descriptives et de divulgation, dans la norme rédactionnelle de la firme
- Agent Contrôle qualité et critique adverse, avec liste de vérification adossée aux PS 110 et 120

**Critère de sortie :** le taux de reprise en revue interne baisse. L’agent 7 devient un passage obligé.

### Phase 4 — Normalisation, modélisation et industrialisation (8 à 12 semaines)

- Agent Normalisation financière, en mode proposition justifiée
- Agent Modélisation, limité aux tests de cohérence et de sensibilité
- Agent Cadrage et conflits
- Tableau de bord des indicateurs; formation de l’équipe; documentation d’exploitation

**Critère de sortie :** deux mandats complets menés à terme de bout en bout sur le dispositif, revus sans écart significatif.

---

# Partie E — Indicateurs de succès

| Indicateur | Mesure | Cible indicative |
|---|---|---|
| Heures par mandat, par type de conclusion | Feuilles de temps, avant et après | Baisse de 20 à 30 % sur les étapes 3, 7 et 11 |
| Délai de la réception des documents à l’émission | Jours civils | Baisse d’au moins 25 % |
| Taux de reprise en revue interne | Corrections significatives par rapport | Baisse continue trimestre après trimestre |
| Complétude de la traçabilité | Part des chiffres du rapport rattachés à une source datée | 100 %, sans exception |
| Écart agent-humain | Divergence entre proposition de l’agent et décision de l’EEE | Suivi, non minimisé : un écart nul signale une revue complaisante |
| Taux d’adoption | Part des mandats menés sur le dispositif | Progression jusqu’à la généralisation |

L’indicateur d’écart agent-humain mérite une attention particulière : il mesure la vigilance de la revue, pas la performance de l’agent. Un écart qui tombe à zéro est un signal d’alarme.

---

# Partie F — Risques et parades

| Risque | Gravité | Parade |
|---|---|---|
| Complaisance de revue — l’EEE valide sans relire | Élevée | Suivi de l’écart agent-humain; revue par les pairs par échantillonnage; l’agent 7 signale les sections validées trop vite |
| Affirmation non étayée passant dans le rapport | Élevée | Règle dure : pas de source, pas de sortie. L’agent 7 bloque l’émission |
| Fuite de données confidentielles | Élevée | Cloisonnement par mandat; hébergement arbitré en phase 0; aucun entraînement sur les données de dossier |
| Dérive normative — le gabarit vieillit | Moyenne | Gabarits versionnés avec date d’effet; revue semestrielle des normes et bulletins |
| Attaque sur la recevabilité en litige | Élevée | Journal d’audit répondant aux trois questions de la section B.6; politique de divulgation appliquée |
| Surinvestissement avant preuve de valeur | Moyenne | Phases à valeur autonome; arrêt possible après toute phase |
| Perte de compétence des juniors | Moyenne | Maintien d’une rotation de mandats exécutés sans assistance; l’apprentissage du métier passe par la mécanique |

---

# Annexe 1 — Décisions à trancher

| # | Décision | Échéance |
|---|---|---|
| 1 | Hébergement au Québec, au Canada ou à l’étranger sous EFVP | Phase 0 |
| 2 | Fournisseur de modèles et clauses de non-entraînement | Phase 0 |
| 3 | Construction interne, adaptation d’une plateforme, ou mixte | Phase 0 |
| 4 | Deux cas d’usage pilotes retenus | Phase 0 |
| 5 | Politique de divulgation de l’usage de l’IA, par palier | Phase 0 |
| 6 | Emploi des normes de l’Institut ou des IVS, par type de mandat | Phase 1 |

# Annexe 2 — Points à valider auprès de l’Institut

Le domaine de l’Institut est bloqué par la politique d’egress du réseau de travail : ni les pages de normes ni le PDF de la PS 100 (2026) n’ont pu être lus directement. Le contenu normatif ci-dessus provient de sources secondaires et de résumés des publications de l’Institut. Les éléments suivants doivent être confirmés sur le texte officiel avant diffusion externe du plan :

- Les intitulés officiels exacts des normes PS 100, 110, 120 et 130 dans leur version française
- Le libellé français officiel de la définition du rapport d’évaluation citée en partie A.2 — la version au présent document est une traduction de travail
- Les paragraphes numérotés de la PS 100 fixant, niveau par niveau, l’ampleur de corroboration indépendante attendue. **C’est le point le plus important à valider** : le paramétrage de l’agent 4 en dépend directement
- La liste complète et à jour des bulletins de pratique en vigueur
- Les exigences chiffrées de formation continue
- Toute ligne directrice sur l’IA publiée depuis le primer de juin 2024

**Levée du blocage :** déposer les PDF des quatre normes dans `docs/normes/` du présent dépôt, ou faire ajouter `cbvinstitute.com` à la liste des domaines autorisés.

# Annexe 3 — Sources

- CBV Institute — [Practice Standard No. 100, version 2026](https://cbvinstitute.com/wp-content/uploads/2025/10/Practice-Standard-No.-100-E-2026.pdf) *(texte officiel, inaccessible depuis l’environnement de travail — à lire hors ligne)*
- CBV Institute — [Practice Standards](https://cbvinstitute.com/members-students/standards-ethics/practice-standards/)
- CBV Institute — [Updated Valuation Practice Standards Now in Effect](https://cbvinstitute.com/news_article/cbv-institutes-updated-valuation-practice-standards-now-in-effect/)
- CBV Institute — [Countdown to 2026 : PS 100, The New Foundation](https://cbvinstitute.com/countdown-to-2026-ps-100-the-new-foundation/)
- CBV Institute — [Countdown to 2026 : Strengthening Report Disclosures](https://cbvinstitute.com/countdown-to-2026-strengthening-report-disclosures-part-1/)
- CBV Institute — [Countdown to 2026 : Scope of Work](https://cbvinstitute.com/countdown-to-2026-scope-of-work-credible-and-properly-supported-valuation-conclusions/)
- CBV Institute — [Troisième et dernier exposé-sondage, normes 100, 110, 120 et 130](https://cbvinstitute.com/wp-content/uploads/2024/12/Exposure-Draft-Revisions-To-Practice-Standards-No-100-110-120-And-130-1.pdf)
- CBV Institute — [Programme d’études des EEE](https://cbvinstitute.com/devenir-un-eee/programme-detudes/?lang=fr) et [Adhésion](https://cbvinstitute.com/adhesion/?lang=fr)
- CBV Institute — [Primer on Artificial Intelligence, juin 2024](https://cbvinstitute.com/wp-content/uploads/2024/06/AI-Primer-June-2024-Final-EN.pdf)
- CBV Institute — [Landmark Decision to Adopt International Valuation Standards](https://cbvinstitute.com/news_article/cbv-institute-announces-landmark-decision-to-adopt-international-valuation-standards/)
- Business Valuation Resources — [The Valuation Profession Responds to AI](https://www.bvresources.com/blogs/bvwire-news/2025/11/25/the-valuation-profession-responds-to-ai-education-is-the-new-standard) et [AI in Business Valuation : Why the Big Four Are Treating It Like a Junior Analyst](https://www.bvresources.com/blogs/bvwire-news/2026/03/17/ai-in-business-valuation-why-the-big-four-are-treating-it-like-a-junior-analyst)
- International Valuation Standards Council — [Navigating the Rise of AI in Valuation](https://ivsc.org/navigating-the-rise-of-ai-in-valuation-opportunities-risks-and-standards/)
- Code de procédure civile, RLRQ c C-25.01 — [art. 22](https://lpc.quebec/articles/art-22-cpc/), [art. 231](https://lpc.quebec/articles/art-231-cpc/), [art. 235](https://lpc.quebec/articles/art-235-cpc/)
- Commission d’accès à l’information — [Principaux changements apportés par la Loi 25](https://www.cai.gouv.qc.ca/protection-renseignements-personnels/sujets-et-domaines-dinteret/principaux-changements-loi-25)

---

*Philippe Prévost, Founding Partner, 1+1 Stratégie*
