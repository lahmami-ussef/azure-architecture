# Tags, locks et quotas

## 1. Définitions simples
| Élément | Rôle | Analogie |
|---|---|---|
| **Tag** | Étiquette nom/valeur sur une ressource | Post-it |
| **Lock** | Empêche la suppression ou la modification | Cadenas |
| **Quota** | Limite d'utilisation par subscription | Plafond de dépense |

## 2. Tags
Exemples : `env=prod`, `owner=equipe-commandes`, `cost-center=1234`. Utiles pour **filtrer, retrouver et répartir les coûts**. Ils ne sont pas hérités par défaut ; on peut forcer l'héritage avec [Azure Policy](../09-governance-and-cost-management/azure-policy.md).

## 3. Locks
- **CanNotDelete** : lecture et modification permises, suppression interdite.
- **ReadOnly** : lecture seule uniquement.
- Un lock s'applique à une ressource, un resource group ou une subscription, et est hérité vers le bas.
- Un lock s'applique **même aux propriétaires** : il faut le retirer pour supprimer.

## 4. Quotas
Limites par subscription et par région (par exemple le nombre de vCPU). Elles protègent contre les erreurs de coût et la surconsommation. Certaines peuvent être augmentées sur demande.

```bash
az group update --name rg-commandes-prod --tags env=prod owner=equipe-commandes
az lock create --name no-delete --lock-type CanNotDelete --resource-group rg-commandes-prod
az vm list-usage --location francecentral -o table
```

Commandes à adapter et tester sur votre compte.

## 5. Erreurs fréquentes
- Ne pas définir de convention de tags dès le départ.
- Poser un lock et oublier qu'il bloque aussi les suppressions légitimes.
- Découvrir un quota atteint au moment d'un déploiement urgent.

## 6. À retenir
- Tags = organiser et suivre les coûts.
- Locks = protéger contre les erreurs.
- Quotas = limites à connaître.

## 7. Questions d'entretien
- Un lock empêche-t-il un propriétaire de supprimer une ressource ?

## 8. QCM
**Q1.** Quel lock empêche seulement la suppression ?
A) ReadOnly B) CanNotDelete C) NoAccess
**Réponse : B.**

**Q2.** Les tags sont-ils hérités par défaut ?
A) Oui B) Non
**Réponse : B.**

## 9. Documentation officielle
- [Tags](https://learn.microsoft.com/azure/azure-resource-manager/management/tag-resources)
- [Locks](https://learn.microsoft.com/azure/azure-resource-manager/management/lock-resources)
- [Quotas](https://learn.microsoft.com/azure/quotas/quotas-overview)
