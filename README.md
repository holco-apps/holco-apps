# HOLCO

HOLCO conçoit et exploite des connecteurs et agents IA pour rendre les données
métier utilisables depuis les assistants déjà choisis par une entreprise. Le
travail porte autant sur les contrôles, les droits et la traçabilité que sur la
restitution conversationnelle.

- Site : [holco.co](https://holco.co)
- Lab technique : [apps.holco.co](https://apps.holco.co)
- Documentation MCP : [holco.co/mcp/docs](https://holco.co/mcp/docs/)
- État des services : [holco.co/status](https://holco.co/status/)
- Signalement de sécurité : [security.txt](https://holco.co/.well-known/security.txt)
- Entité juridique : HOLCO INVEST, SIREN 819 582 453, RCS Paris
- Contact sécurité et RGPD : `privacy@holco.co`

## Projets publics

### [PennyPilot MCP](https://github.com/holco-apps/pennypilot-mcp)

Contrats publics, documentation d'intégration et garde-fous vérifiables du
connecteur comptable HOLCO. Le service distant et sa logique cabinet restent
propriétaires. Le serveur public est déclaré dans le
[registre MCP](https://registry.modelcontextprotocol.io/?search=pennypilot).

### [openRMN](https://github.com/holco-apps/openrmn)

Couche indépendante de mesure Retail Media. Elle harmonise plusieurs sources,
calcule des indicateurs déterministes et expose une surface MCP. Licence MIT.

### [PennyLane Cabinet](https://github.com/holco-apps/pennylane-cabinet)

Extension locale historique pour Claude Desktop, limitée à des outils
Pennylane en lecture seule. Le service remote actuel est documenté séparément.

## Architecture observable

Le [Lab HOLCO](https://apps.holco.co) décrit l'architecture réellement opérée
et distingue les mécanismes en service de la feuille de route :

- frontend Next.js, React et TypeScript exporté statiquement ;
- services Node.js et Python/FastAPI selon les produits ;
- nginx en frontal TLS et services gérés par systemd ;
- SQLite en mode WAL et PostgreSQL selon les usages ;
- connecteurs MCP, OAuth et API avec périmètres d'accès séparés ;
- contrôles déterministes, journalisation technique et validation humaine pour
  les décisions engageantes.

Les versions courantes, les flux de données et les limites connues sont publiés
dans le Lab plutôt que recopiés ici afin d'éviter plusieurs références
contradictoires.

## Sécurité et données

Les engagements dépendent du produit et du mandat client. Les connecteurs
comptables publiés comme tels sont conçus en lecture seule. Les secrets sont
séparés des dépôts, les jetons serveur sont chiffrés au repos et les services
applicatifs restent derrière le reverse proxy. Les traitements, durées de
conservation et rôles RGPD sont détaillés dans la
[politique de confidentialité](https://holco.co/confidentialite/) et dans la
[documentation sécurité](https://holco.co/securite/).

HOLCO ne présente pas un prototype, une cible ou une compatibilité envisagée
comme une capacité déjà généralisée. Les données clients et la logique métier
propriétaire ne sont pas publiées dans cette organisation GitHub.

## Politique de publication

Nous publions les contrats, exemples et composants qui peuvent être audités
sans exposer les données d'un client ni son processus métier. Les services,
secrets, configurations de production et règles propres aux clients restent
privés.

Contact : `alan@holco.co` · DPO : Pierre Coquard (`privacy@holco.co`).
