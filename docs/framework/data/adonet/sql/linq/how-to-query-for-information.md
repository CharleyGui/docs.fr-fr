---
title: 'Procédure : Demander des informations'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793534"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="99983-102">Procédure : Demander des informations</span><span class="sxs-lookup"><span data-stu-id="99983-102">How to: Query for Information</span></span>
<span data-ttu-id="99983-103">Les requêtes effectuées dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent la même syntaxe que les requêtes effectuées dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99983-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="99983-104">La seule différence est que les objets référencés dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] les requêtes sont mappés aux éléments d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="99983-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="99983-105">Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="99983-105">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="99983-106">traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement.</span><span class="sxs-lookup"><span data-stu-id="99983-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="99983-107">Certaines fonctionnalités de requêtes [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] peuvent nécessiter une attention particulière dans les applications [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99983-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="99983-108">Pour plus d’informations, consultez [concepts de requête](query-concepts.md).</span><span class="sxs-lookup"><span data-stu-id="99983-108">For more information, see [Query Concepts](query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99983-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="99983-109">Example</span></span>  
 <span data-ttu-id="99983-110">La requête suivante demande une liste de clients de Londres.</span><span class="sxs-lookup"><span data-stu-id="99983-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="99983-111">Dans cet exemple, `Customers` est une table de l'exemple de base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="99983-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="99983-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99983-112">See also</span></span>

- [<span data-ttu-id="99983-113">Création du modèle objet</span><span class="sxs-lookup"><span data-stu-id="99983-113">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="99983-114">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="99983-114">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="99983-115">Interrogation de la base de données</span><span class="sxs-lookup"><span data-stu-id="99983-115">Querying the Database</span></span>](querying-the-database.md)
