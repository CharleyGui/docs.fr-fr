---
title: 'Exemples de syntaxe de requête basée sur une méthode : parcours des relations'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: bb40d10165592b25cc6afc1eac799a05b4504e8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191967"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="dc5dc-102">Exemples de syntaxe de requête basée sur une méthode : parcours des relations</span><span class="sxs-lookup"><span data-stu-id="dc5dc-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="dc5dc-103">Les propriétés de navigation dans le Entity Framework sont des propriétés de raccourci utilisées pour rechercher les entités aux terminaisons d’une association.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="dc5dc-104">Les propriétés de navigation permettent à un utilisateur de naviguer d'une entité à une autre ou d'une entité à des entités associées par le biais d'un ensemble d'associations.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="dc5dc-105">Cette rubrique fournit des exemples de syntaxe de requête fondée sur une méthode montrant comment parcourir les relations à l’aide des propriétés de navigation dans LINQ to Entities des requêtes.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="dc5dc-106">Le modèle de vente AdventureWorks Sales Model utilisé dans ces exemples est construit à partir des tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dc5dc-107">Les exemples de cette rubrique utilisent les `using` / `Imports` instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dc5dc-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="dc5dc-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5dc-108">Example</span></span>  

 <span data-ttu-id="dc5dc-109">L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.SelectMany%2A> pour obtenir toutes les commandes des contacts dont le nom de famille est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="dc5dc-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="dc5dc-110">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="dc5dc-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5dc-111">Example</span></span>  

 <span data-ttu-id="dc5dc-112">L'exemple suivant de syntaxe de requête fondée sur une méthode utilise la méthode <xref:System.Linq.Queryable.Select%2A> pour obtenir tous les ID de contact et la somme du montant total dû pour chaque contact dont le nom est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="dc5dc-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="dc5dc-113">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="dc5dc-114">La méthode `Sum` utilise la propriété de navigation `Contact.SalesOrderHeader` pour calculer la somme du montant total dû pour l'ensemble des commandes de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="dc5dc-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5dc-115">Example</span></span>  

 <span data-ttu-id="dc5dc-116">L'exemple suivant de syntaxe de requête fondée sur une méthode obtient toutes les commandes des contacts dont le nom de famille est « Zhou ».</span><span class="sxs-lookup"><span data-stu-id="dc5dc-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="dc5dc-117">La propriété de navigation `Contact.SalesOrderHeader` est utilisée pour obtenir la collection des objets `SalesOrderHeader` de chaque contact.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="dc5dc-118">Le nom et les commandes du contact sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="dc5dc-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5dc-119">Example</span></span>  

 <span data-ttu-id="dc5dc-120">L’exemple ci-dessous utilise les propriétés de navigation `SalesOrderHeader.Address` et `SalesOrderHeader.Contact` pour obtenir la collection des objets `Address` et `Contact` associés à chaque commande.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="dc5dc-121">Le nom du contact, l'adresse, le numéro de commande et le montant total dû de chaque commande pour la ville de Seattle sont retournés dans un type anonyme.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="dc5dc-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="dc5dc-122">Example</span></span>  

 <span data-ttu-id="dc5dc-123">L'exemple ci-dessous utilise la méthode `Where` pour rechercher des commandes qui ont été passées après le 1er décembre 2003, puis utilise la propriété de navigation `order.SalesOrderDetail` pour obtenir les détails de chaque commande.</span><span class="sxs-lookup"><span data-stu-id="dc5dc-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="dc5dc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc5dc-124">See also</span></span>

- [<span data-ttu-id="dc5dc-125">Relations, propriétés de navigation et clés étrangères</span><span class="sxs-lookup"><span data-stu-id="dc5dc-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="dc5dc-126">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="dc5dc-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
