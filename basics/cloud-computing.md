# Cloud computing et modèles de déploiement

## 1. Définition simple
Le **cloud computing** consiste à louer des ressources informatiques (serveurs, stockage, bases de données) via Internet, à la demande, et à ne payer que ce qu'on utilise.

> Analogie : comme l'électricité, on ne construit pas sa centrale, on paie sa consommation.

## 2. Ce que ça change
| | On-premises (CapEx) | Cloud (OpEx) |
|---|---|---|
| Paiement | Achat de matériel au départ | Paiement à l'usage |
| Capacité | Dimensionnée pour le pic | Ajustée à la demande |
| Mise à disposition | Semaines ou mois | Minutes |

## 3. Modèles de déploiement
| Modèle | Définition | Exemple |
|---|---|---|
| Public | Ressources d'un fournisseur, partagées | Azure |
| Privé | Infrastructure dédiée à une organisation | Datacenter interne |
| Hybride | On-premises + cloud public | Base locale + front sur Azure |
| Multicloud | Plusieurs fournisseurs | Azure + AWS |

```mermaid
flowchart LR
    OnPrem[On-premises] <-->|VPN / ExpressRoute| Azure[Azure]
    Azure <--> Other[Autre cloud]
```

Le lien hybride se fait par VPN ou ExpressRoute ([chapitre 4](../04-networking/vpn-gateway-and-expressroute.md)).

## 4. À retenir
- Cloud = ressources à la demande, payées à l'usage.
- CapEx (achat) devient OpEx (consommation).
- Hybride = local + cloud ; multicloud = plusieurs fournisseurs.

## 5. Questions d'entretien
- Quelle différence entre hybride et multicloud ?
- Pourquoi le cloud n'est-il pas toujours moins cher ?

## 6. QCM
**Q1.** Quel terme décrit le paiement à l'usage ?
A) CapEx B) OpEx C) SLA D) RTO
**Réponse : B.**

**Q2.** Base de données en local + front sur Azure : quel modèle ?
A) Privé B) Public C) Hybride D) Multicloud
**Réponse : C.**

## 7. Documentation officielle
- [Qu'est-ce que le cloud computing ?](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-is-cloud-computing)
