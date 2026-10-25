# Outils Azure

## 1. Définition simple
Il existe plusieurs façons de piloter Azure, mais toutes passent par le même moteur : [Azure Resource Manager](../02-azure-resource-organization/azure-resource-manager.md).

## 2. Les outils
| Outil | Usage |
|---|---|
| Azure Portal | Interface web, pour explorer |
| Cloud Shell | Terminal dans le navigateur, sans installation |
| Azure CLI | Commandes `az`, pour les scripts |
| Azure PowerShell | Cmdlets `Az`, pour PowerShell |
| SDK | Utiliser Azure depuis son code |
| REST API | API sous-jacente |

## 3. Premières commandes
Prérequis : un compte Azure. Exemples à adapter et à tester sur votre compte.

```bash
az login
az account show
az group create --name rg-guide-demo --location francecentral
az group delete --name rg-guide-demo --yes   # nettoyage
```

```powershell
Connect-AzAccount
New-AzResourceGroup -Name rg-guide-demo -Location francecentral
Remove-AzResourceGroup -Name rg-guide-demo -Force   # nettoyage
```

Remplacez le nom et la région. Supprimez toujours vos ressources de test.

## 4. À retenir
- Portal pour comprendre, CLI ou code pour reproduire.
- En production, préférer l'Infrastructure as Code ([Bicep](../08-devops-and-infrastructure-as-code/bicep.md)).

## 5. Questions d'entretien
- Pourquoi éviter de tout configurer à la main dans le Portal ?

## 6. QCM
**Q1.** Quel outil offre un terminal sans installation ?
A) Cloud Shell B) SDK C) Bicep
**Réponse : A.**

**Q2.** Quel composant traite toutes les requêtes de création de ressources ?
A) Azure Resource Manager B) Azure Monitor C) Azure Policy
**Réponse : A.**

## 7. Documentation officielle
- [Azure CLI](https://learn.microsoft.com/cli/azure/)
- [Cloud Shell](https://learn.microsoft.com/azure/cloud-shell/overview)
