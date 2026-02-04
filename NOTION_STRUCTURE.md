# Structure Notion - Cresceo

**Objectif** : Migrer la documentation Docsify vers Notion pour un travail collaboratif.

---

## Architecture proposée

```
Cresceo (Workspace)
│
├── Dashboard
│   └── Vue d'ensemble projet (liens rapides, KPIs, prochaines étapes)
│
├── Stratégie
│   ├── Business Plan
│   ├── Contexte Projet
│   ├── Pacte Associés (draft)
│   └── Analyse Marché
│
├── Opérationnel
│   ├── Plan de Lancement
│   ├── Pipe Commercial (database)
│   └── Contacts (database)
│
├── Ateliers & CRs
│   ├── Template CR (template)
│   ├── CR BP 04/02
│   ├── CR MKG 04/02
│   ├── Agenda Lyon 27/02
│   └── [Futurs CRs...]
│
├── Marketing
│   ├── Brief Identité Visuelle
│   ├── Charte Graphique (après validation)
│   └── Contenus (articles, posts)
│
└── Admin
    ├── Ressources (liens, docs externes)
    └── Archive
```

---

## Databases à créer

### 1. Pipe Commercial

| Propriété | Type | Options |
|-----------|------|---------|
| Nom client | Title | - |
| Statut | Select | Prospect, Qualifié, Devis envoyé, Gagné, Perdu |
| Canal | Select | CAD42, Réseau Igor, Réseau Julien, Réseau Baptiste, Impulse, Autre |
| Valeur | Number | € |
| Date contact | Date | - |
| Prochaine action | Text | - |
| Responsable | Person | - |

### 2. Contacts

| Propriété | Type | Options |
|-----------|------|---------|
| Nom | Title | - |
| Entreprise | Text | - |
| Rôle | Text | - |
| Email | Email | - |
| LinkedIn | URL | - |
| Type | Select | Client, Partenaire, Formateur, Institutionnel |
| Notes | Text | - |

### 3. Actions (TODO)

| Propriété | Type | Options |
|-----------|------|---------|
| Action | Title | - |
| Statut | Select | À faire, En cours, Fait, Bloqué |
| Responsable | Person | - |
| Échéance | Date | - |
| Priorité | Select | Haute, Moyenne, Basse |
| Lié à | Relation | (vers Ateliers ou Projets) |

---

## Templates à créer

### Template CR Atelier

```
# CR [Nom Atelier] - [Date]

## Participants
- [ ] Participant 1
- [ ] Participant 2

## Décisions prises
1. ...
2. ...

## Actions
| Action | Responsable | Échéance |
|--------|-------------|----------|
| ... | ... | ... |

## Points en suspens
- ...

## Prochaine réunion
- Date :
- Objet :
```

---

## Migration depuis Docsify

### Documents à importer

| Document Docsify | Page Notion cible |
|------------------|-------------------|
| Business Plan Organisme Formation IA.md | Stratégie / Business Plan |
| CONTEXTE_PROJET.md | Stratégie / Contexte Projet |
| PACTE_ASSOCIES_DRAFT.md | Stratégie / Pacte Associés |
| ANALYSE_MARCHE.md | Stratégie / Analyse Marché |
| PLAN_LANCEMENT_CRESCEO.md | Opérationnel / Plan de Lancement |
| CR_ATELIER_BP_2026-02-04.md | Ateliers & CRs / CR BP 04/02 |
| CR_ATELIER_MKG_2026-02-04.md | Ateliers & CRs / CR MKG 04/02 |
| ATELIER_MARCHE_PROSPECTION_AGENDA.md | Ateliers & CRs / Agenda Lyon 27/02 |

### Process de migration

1. **Créer le workspace** Notion "Cresceo"
2. **Inviter les membres** : Igor, Julien, Baptiste, Éloïse, JP, Raph
3. **Créer la structure** (pages et databases)
4. **Copier/coller** les contenus MD (Notion parse bien le Markdown)
5. **Configurer les templates** (CR, etc.)
6. **Archiver Docsify** (garder GitHub Pages en backup si besoin)

---

## Paramètres recommandés

### Permissions

| Membre | Niveau | Notes |
|--------|--------|-------|
| Igor, Baptiste, Julien | Full access | Associés actifs |
| Éloïse | Can edit | Marketing |
| JP, Raph | Can comment | Passifs - consultation |

### Intégrations utiles

- **Slack/Discord** : Notifications sur modifications
- **Google Calendar** : Sync dates ateliers
- **Zapier** : Automatisations (optionnel)

---

## Prochaines étapes

- [ ] Baptiste crée le workspace Notion
- [ ] Baptiste importe les docs principaux
- [ ] Baptiste configure les databases (Pipe, Contacts, Actions)
- [ ] Tester avec l'équipe
- [ ] Décider sort de Docsify (archive ou suppression)

---

*Document de référence pour la mise en place Notion - 4 février 2026*
