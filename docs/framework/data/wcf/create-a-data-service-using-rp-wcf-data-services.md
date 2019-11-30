---
title: "Comment : créer un service de données à l'aide du fournisseur de réflexion (services de données WCF)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569292"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="355b0-102">Comment : créer un service de données à l'aide du fournisseur de réflexion (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="355b0-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="355b0-103">WCF Data Services vous permet de définir un modèle de données basé sur des classes arbitraires tant que ces classes sont exposées comme des objets qui implémentent l’interface <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="355b0-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="355b0-104">Pour plus d’informations, consultez [Data Services des fournisseurs](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="355b0-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="355b0-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="355b0-105">Example</span></span>  
 <span data-ttu-id="355b0-106">L'exemple suivant définit un modèle de données qui inclut `Orders` et `Items`.</span><span class="sxs-lookup"><span data-stu-id="355b0-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="355b0-107">La classe de conteneur d'entités  `OrderItemData` a deux méthodes publiques qui retournent des interfaces <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="355b0-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="355b0-108">Ces interfaces sont les jeux d'entités des types d'entité `Orders` et `Items`.</span><span class="sxs-lookup"><span data-stu-id="355b0-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="355b0-109">Un `Order` peut inclure plusieurs `Items`, donc le type d’entité `Orders` a une propriété de navigation `Items` qui retourne une collection d’objets `Items`.</span><span class="sxs-lookup"><span data-stu-id="355b0-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="355b0-110">La classe de conteneur d'entités `OrderItemData` est le type générique de la classe <xref:System.Data.Services.DataService%601> d'où est dérivé le service de données `OrderItems`.</span><span class="sxs-lookup"><span data-stu-id="355b0-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="355b0-111">Comme cet exemple illustre un fournisseur de données en mémoire et que les modifications ne sont pas persistantes en dehors des instances de l'objet actuelles, l'implémentation de l'interface <xref:System.Data.Services.IUpdatable> n'apporte aucun avantage.</span><span class="sxs-lookup"><span data-stu-id="355b0-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="355b0-112">Pour obtenir un exemple qui implémente l’interface <xref:System.Data.Services.IUpdatable>, consultez [Comment : créer un service de données à l’aide d’une source de données LINQ to SQL](create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="355b0-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="355b0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="355b0-113">See also</span></span>

- [<span data-ttu-id="355b0-114">Guide pratique pour créer un service de données à l’aide d’une source de données LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="355b0-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="355b0-115">Fournisseurs de services de données</span><span class="sxs-lookup"><span data-stu-id="355b0-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="355b0-116">Guide pratique pour créer un service de données à l’aide d’une source de données Entity Framework ADO.NET</span><span class="sxs-lookup"><span data-stu-id="355b0-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
