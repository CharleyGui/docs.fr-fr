---
title: Mise en cache d'un plan de requête (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 51c5de8365819065f8e505468f37a47370ec502f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91175549"
---
# <a name="query-plan-caching-entity-sql"></a>Mise en cache d'un plan de requête (Entity SQL)

À chaque tentative d'exécution d'une requête, le pipeline de la requête recherche son cache de plan de requête pour voir si la requête exacte est déjà compilée et disponible. Si tel est le cas, il réutilise le plan mis en cache plutôt que d'en générer un nouveau. Si aucune correspondance n'est trouvée dans le cache du plan de requête, la requête est compilée et mise en cache. Une requête est identifiée par son texte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et sa collection de paramètres (noms et types). Toutes les comparaisons de texte respectent la casse.  
  
## <a name="configuration"></a>Configuration  

 La mise en cache du plan de requête est configurable par le biais de <xref:System.Data.EntityClient.EntityCommand>.  
  
 Pour activer ou désactiver la mise en cache du plan de requête par le biais de <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, affectez à cette propriété la valeur `true` ou `false`. La désactivation de la mise en cache du plan pour les requêtes dynamiques individuelles qui ne seront probablement pas utilisées plus d'une fois améliore les performances.  
  
 Vous pouvez activer la mise en cache du plan de requête via <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.  
  
## <a name="recommended-practice"></a>Pratique recommandée  

 Les requêtes dynamiques doivent être évitées, en général. L’exemple de requête dynamique suivant est vulnérable aux attaques par injection de code SQL, car il accepte directement l’entrée utilisateur sans aucune validation.  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 Si vous utilisez des requêtes générées dynamiquement, pensez à désactiver la mise en cache du plan de requête pour éviter une consommation inutile de mémoire pour les entrées de cache qui ne seront probablement pas réutilisées.  
  
 La mise en cache du plan de requête sur les requêtes statiques et les requêtes paramétrables peut fournir des avantages en matière de performances. L'exemple ci-dessous illustre une requête statique :  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 Pour que les requêtes soient mappées correctement par le cache du plan de requête, elles doivent satisfaire les exigences suivantes :  
  
- Le texte de requête doit être un modèle constant, de préférence une chaîne ou une ressource constante.  
  
- <xref:System.Data.EntityClient.EntityParameter> ou <xref:System.Data.Objects.ObjectParameter> doit être utilisé partout où une valeur fournie par l'utilisateur doit être transmise.  
  
 Vous devez éviter les modèles de requête suivants, qui consomment inutilement des emplacements dans le cache du plan de requête :  
  
- modifications de la casse du texte ;  
  
- modifications des espaces blancs ;  
  
- modifications des valeurs littérales ;  
  
- modifications du texte à l'intérieur des commentaires.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'Entity SQL](entity-sql-overview.md)
