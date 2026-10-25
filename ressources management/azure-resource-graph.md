# Azure Resource Graph

## 1. Définition simple
**Azure Resource Graph** permet d'interroger rapidement toutes ses ressources, sur plusieurs subscriptions, avec des requêtes de type KQL.

> Analogie : un moteur de recherche pour son infrastructure.

## 2. À quoi ça sert
- Compter et lister les ressources par type, région ou tag.
- Trouver les ressources non conformes ou sans tag.
- Faire des inventaires à grande échelle, sans parcourir chaque subscription.

## 3. Exemples de requêtes
```kusto
Resources
| summarize count() by type
```
```kusto
Resources
| where isempty(tags['env'])
| project name, type, resourceGroup, location
```

Avec la CLI (extension à installer) :
```bash
az extension add --name resource-graph
az graph query -q "Resources | summarize count() by type"
```
À tester sur votre compte. On peut aussi utiliser **Azure Resource Graph Explorer** dans le Portal.

## 4. Limites
Resource Graph donne l'état des ressources, pas leur historique de modifications détaillé. Les résultats sont limités à ce que votre compte a le droit de voir.

## 5. À retenir
- Une seule requête pour tout l'inventaire.
- Les tags rendent les requêtes beaucoup plus utiles.

## 6. Questions d'entretien
- Comment retrouver toutes les ressources sans tag `env` ?

## 7. QCM
**Q1.** Quel service permet d'interroger les ressources sur plusieurs subscriptions ?
A) Azure Resource Graph B) Azure Advisor C) Azure Policy
**Réponse : A.**

**Q2.** Quel langage sert aux requêtes ?
A) SQL uniquement B) Un langage de type KQL C) Bicep
**Réponse : B.**

## 8. Documentation officielle
- [Azure Resource Graph](https://learn.microsoft.com/azure/governance/resource-graph/overview)
