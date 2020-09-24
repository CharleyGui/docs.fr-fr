---
title: 'Procédure : Demander des informations'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166402"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="79f33-102">Procédure : Demander des informations</span><span class="sxs-lookup"><span data-stu-id="79f33-102">How to: Query for Information</span></span>

<span data-ttu-id="79f33-103">Les requêtes dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent la même syntaxe que les requêtes dans LINQ.</span><span class="sxs-lookup"><span data-stu-id="79f33-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in LINQ.</span></span> <span data-ttu-id="79f33-104">La seule différence est que les objets référencés dans les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes sont mappés aux éléments d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="79f33-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="79f33-105">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="79f33-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="79f33-106">traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement.</span><span class="sxs-lookup"><span data-stu-id="79f33-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="79f33-107">Certaines fonctionnalités des requêtes LINQ peuvent nécessiter une attention particulière dans les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="79f33-107">Some features of LINQ queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="79f33-108">Pour plus d’informations, consultez [concepts de requête](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="79f33-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79f33-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="79f33-109">Example</span></span>  

 <span data-ttu-id="79f33-110">La requête suivante demande une liste de clients de Londres.</span><span class="sxs-lookup"><span data-stu-id="79f33-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="79f33-111">Dans cet exemple, `Customers` est une table de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="79f33-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="79f33-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79f33-112">See also</span></span>

- [<span data-ttu-id="79f33-113">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="79f33-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="79f33-114">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="79f33-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="79f33-115">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="79f33-115">Querying the Database</span></span>](querying-the-database.md)
