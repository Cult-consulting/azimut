# Guide Configuration Zoho Mail + DNS OVH

**Domaine** : cresceo.fr
**Service** : Zoho Mail Free (5 utilisateurs)

---

## Étape 1 : Créer le compte Zoho Mail

1. Aller sur https://www.zoho.com/mail/zohomail-pricing.html
2. Cliquer sur **"Forever Free Plan"** (5 users, 5GB/user)
3. S'inscrire avec le domaine `cresceo.fr`
4. Créer le premier compte admin (ex: `contact@cresceo.fr` ou `igor@cresceo.fr`)

---

## Étape 2 : Vérifier la propriété du domaine

Zoho propose plusieurs méthodes. **La plus simple avec OVH** : enregistrement TXT.

### Dans Zoho
1. Zoho affiche un code de vérification (ex: `zoho-verification=zb12345678.zmverify.zoho.eu`)
2. Copier ce code

### Dans OVH
1. Aller sur https://www.ovh.com/manager/
2. **Web Cloud** → **Noms de domaine** → **cresceo.fr**
3. Onglet **Zone DNS**
4. Cliquer **Ajouter une entrée**
5. Choisir **TXT**
6. Laisser le sous-domaine vide (ou `@`)
7. Coller le code Zoho dans **Valeur**
8. TTL : 3600 (par défaut)
9. **Valider**

⏳ Attendre 5-15 min, puis cliquer **Vérifier** dans Zoho.

---

## Étape 3 : Configurer les enregistrements MX

### Supprimer les MX existants (si présents)
Dans OVH Zone DNS, supprimer toute entrée MX existante.

### Ajouter les MX Zoho

| Type | Sous-domaine | Priorité | Valeur | TTL |
|------|--------------|----------|--------|-----|
| MX | (vide) | 10 | `mx.zoho.eu` | 3600 |
| MX | (vide) | 20 | `mx2.zoho.eu` | 3600 |
| MX | (vide) | 50 | `mx3.zoho.eu` | 3600 |

---

## Étape 4 : Configurer SPF (anti-spam sortant)

### Ajouter enregistrement TXT pour SPF

| Type | Sous-domaine | Valeur | TTL |
|------|--------------|--------|-----|
| TXT | (vide) | `v=spf1 include:zoho.eu ~all` | 3600 |

---

## Étape 5 : Configurer DKIM (signature emails)

1. Dans Zoho Mail Admin : **Email Authentication** → **DKIM**
2. Cliquer **Add** pour cresceo.fr
3. Copier la clé DKIM générée

### Ajouter dans OVH

| Type | Sous-domaine | Valeur | TTL |
|------|--------------|--------|-----|
| TXT | `zmail._domainkey` | (coller la clé DKIM) | 3600 |

---

## Étape 6 : Créer les comptes utilisateurs

Dans Zoho Mail Admin → **Users** → **Add User**

| Email | Utilisateur |
|-------|-------------|
| `igor@cresceo.fr` | Igor Cannone |
| `baptiste@cresceo.fr` | Baptiste Casnedi |
| `julien@cresceo.fr` | Julien Gardette |
| `eloise@cresceo.fr` | Éloïse Bouveret |
| `contact@cresceo.fr` | Alias ou boîte partagée |

**Note** : 5 utilisateurs max sur le plan gratuit. `contact@` peut être un alias vers `igor@`.

---

## Récapitulatif DNS OVH Final

| Type | Sous-domaine | Valeur |
|------|--------------|--------|
| TXT | (vide) | `zoho-verification=...` |
| MX | (vide) | `mx.zoho.eu` (prio 10) |
| MX | (vide) | `mx2.zoho.eu` (prio 20) |
| MX | (vide) | `mx3.zoho.eu` (prio 50) |
| TXT | (vide) | `v=spf1 include:zoho.eu ~all` |
| TXT | `zmail._domainkey` | (clé DKIM) |

---

## Test final

1. Envoyer un email depuis `igor@cresceo.fr` vers une adresse Gmail
2. Vérifier réception
3. Répondre pour tester la réception entrante
4. Vérifier sur https://www.mail-tester.com (score 10/10 visé)

---

## Délais de propagation

- Vérification domaine : 5-15 min
- MX : 15-60 min
- SPF/DKIM : 1-4 heures (parfois jusqu'à 24h)

---

*Guide créé le 4 février 2026*
