---
title: Mise en cache d'un plan de requête (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: a0e84f40aed2cff146e4e203cca73a9110de0e2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149984"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="761b3-102">Mise en cache d'un plan de requête (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="761b3-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="761b3-103">À chaque tentative d'exécution d'une requête, le pipeline de la requête recherche son cache de plan de requête pour voir si la requête exacte est déjà compilée et disponible.</span><span class="sxs-lookup"><span data-stu-id="761b3-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="761b3-104">Si tel est le cas, il réutilise le plan mis en cache plutôt que d'en générer un nouveau.</span><span class="sxs-lookup"><span data-stu-id="761b3-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="761b3-105">Si aucune correspondance n'est trouvée dans le cache du plan de requête, la requête est compilée et mise en cache.</span><span class="sxs-lookup"><span data-stu-id="761b3-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="761b3-106">Une requête est identifiée par son texte [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et sa collection de paramètres (noms et types).</span><span class="sxs-lookup"><span data-stu-id="761b3-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="761b3-107">Toutes les comparaisons de texte respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="761b3-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="761b3-108">Configuration</span><span class="sxs-lookup"><span data-stu-id="761b3-108">Configuration</span></span>  
 <span data-ttu-id="761b3-109">La mise en cache du plan de requête est configurable par le biais de <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="761b3-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="761b3-110">Pour activer ou désactiver la mise en cache du plan de requête par le biais de <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, affectez à cette propriété la valeur `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="761b3-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="761b3-111">La désactivation de la mise en cache du plan pour les requêtes dynamiques individuelles qui ne seront probablement pas utilisées plus d'une fois améliore les performances.</span><span class="sxs-lookup"><span data-stu-id="761b3-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="761b3-112">Vous pouvez activer la mise en cache du plan de requête via <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="761b3-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="761b3-113">Pratique recommandée</span><span class="sxs-lookup"><span data-stu-id="761b3-113">Recommended Practice</span></span>  
 <span data-ttu-id="761b3-114">Les requêtes dynamiques doivent être évitées, en général.</span><span class="sxs-lookup"><span data-stu-id="761b3-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="761b3-115">L’exemple de requête dynamique suivant est vulnérable aux attaques par injection de code SQL, car il accepte directement l’entrée utilisateur sans aucune validation.</span><span class="sxs-lookup"><span data-stu-id="761b3-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 ```csharp
 var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;  
 ```

 <span data-ttu-id="761b3-116">Si vous utilisez des requêtes générées dynamiquement, pensez à désactiver la mise en cache du plan de requête pour éviter une consommation inutile de mémoire pour les entrées de cache qui ne seront probablement pas réutilisées.</span><span class="sxs-lookup"><span data-stu-id="761b3-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="761b3-117">La mise en cache du plan de requête sur les requêtes statiques et les requêtes paramétrables peut fournir des avantages en matière de performances.</span><span class="sxs-lookup"><span data-stu-id="761b3-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="761b3-118">L'exemple ci-dessous illustre une requête statique :</span><span class="sxs-lookup"><span data-stu-id="761b3-118">The following is an example of a static query:</span></span>  
  
```csharp
var query = "SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="761b3-119">Pour que les requêtes soient mappées correctement par le cache du plan de requête, elles doivent satisfaire les exigences suivantes :</span><span class="sxs-lookup"><span data-stu-id="761b3-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="761b3-120">Le texte de requête doit être un modèle constant, de préférence une chaîne ou une ressource constante.</span><span class="sxs-lookup"><span data-stu-id="761b3-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="761b3-121"><xref:System.Data.EntityClient.EntityParameter> ou <xref:System.Data.Objects.ObjectParameter> doit être utilisé partout où une valeur fournie par l'utilisateur doit être transmise.</span><span class="sxs-lookup"><span data-stu-id="761b3-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="761b3-122">Vous devez éviter les modèles de requête suivants, qui consomment inutilement des emplacements dans le cache du plan de requête :</span><span class="sxs-lookup"><span data-stu-id="761b3-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="761b3-123">modifications de la casse du texte ;</span><span class="sxs-lookup"><span data-stu-id="761b3-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="761b3-124">modifications des espaces blancs ;</span><span class="sxs-lookup"><span data-stu-id="761b3-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="761b3-125">modifications des valeurs littérales ;</span><span class="sxs-lookup"><span data-stu-id="761b3-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="761b3-126">modifications du texte à l'intérieur des commentaires.</span><span class="sxs-lookup"><span data-stu-id="761b3-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="761b3-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="761b3-127">See also</span></span>

- [<span data-ttu-id="761b3-128">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="761b3-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
