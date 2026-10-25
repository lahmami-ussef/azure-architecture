# Resource Providers et types de ressources

## 1. Définition simple
Un **resource provider** est le service qui fournit un type de ressource donné. Chaque ressource Azure a un **type** de la forme `Fournisseur/type`.

## 2. Exemples
| Type de ressource | Provider |
|---|---|
| `Microsoft.Compute/virtualMachines` | `Microsoft.Compute` |
| `Microsoft.Storage/storageAccounts` | `Microsoft.Storage` |
| `Microsoft.Web/sites` | `Microsoft.Web` |
| `Microsoft.Sql/servers` | `Microsoft.Sql` |

## 3. Ce qu'il faut savoir
- Un provider doit être **enregistré** dans la subscription avant d'être utilisé ; beaucoup le sont déjà.
- Chaque type a des **versions d'API** : on les retrouve dans les templates.
- Ce nom de type apparaît partout : templates, policies, requêtes.

```bash
az provider list --query "[?registrationState=='Registered'].namespace" -o table
az provider register --namespace Microsoft.Compute
```

À tester sur votre compte ; l'enregistrement peut prendre quelques minutes.

## 4. Erreurs fréquentes
- Erreur de déploiement « provider non enregistré » : il suffit de l'enregistrer.
- Confondre le type (`virtualMachines`) et le nom de la ressource (`vm-api-01`).

## 5. À retenir
- Type = `Provider/type`.
- Un provider doit être enregistré pour être utilisé.

## 6. Questions d'entretien
- Que signifie `Microsoft.Storage/storageAccounts` ?

## 7. QCM
**Q1.** `Microsoft.Compute` est :
A) Une région B) Un resource provider C) Un tag
**Réponse : B.**

**Q2.** Si un déploiement échoue car un provider n'est pas disponible, que faire ?
A) Le supprimer B) L'enregistrer C) Changer de tenant
**Réponse : B.**

## 8. Documentation officielle
- [Resource providers et types](https://learn.microsoft.com/azure/azure-resource-manager/management/resource-providers-and-types)
