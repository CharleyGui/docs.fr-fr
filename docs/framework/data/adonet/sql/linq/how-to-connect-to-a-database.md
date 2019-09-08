---
title: 'Procédure : Se connecter à une base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c33d74b3-530d-421b-a121-96786dd263a5
ms.openlocfilehash: 48ff4af2c881104d5699910e20ef86eea0466d2a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793860"
---
# <a name="how-to-connect-to-a-database"></a><span data-ttu-id="5df12-102">Procédure : Se connecter à une base de données</span><span class="sxs-lookup"><span data-stu-id="5df12-102">How to: Connect to a Database</span></span>
<span data-ttu-id="5df12-103">Le <xref:System.Data.Linq.DataContext> est le conduit principal par lequel vous vous connectez à une base de données, récupérez des objets de celle-ci et soumettez des modifications.</span><span class="sxs-lookup"><span data-stu-id="5df12-103">The <xref:System.Data.Linq.DataContext> is the main conduit by which you connect to a database, retrieve objects from it, and submit changes back to it.</span></span> <span data-ttu-id="5df12-104">Vous utilisez le <xref:System.Data.Linq.DataContext> tout comme vous utiliseriez un ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="5df12-104">You use the <xref:System.Data.Linq.DataContext> just as you would use an ADO.NET <xref:System.Data.SqlClient.SqlConnection>.</span></span> <span data-ttu-id="5df12-105">En fait, le <xref:System.Data.Linq.DataContext> est initialisé avec une connexion ou une chaîne de connexion que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="5df12-105">In fact, the <xref:System.Data.Linq.DataContext> is initialized with a connection or connection string that you supply.</span></span> <span data-ttu-id="5df12-106">Pour plus d’informations, consultez [méthodes DataContext (Concepteur O/R)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span><span class="sxs-lookup"><span data-stu-id="5df12-106">For more information, see [DataContext Methods (O/R Designer)](/visualstudio/data-tools/datacontext-methods-o-r-designer).</span></span>  
  
 <span data-ttu-id="5df12-107">Le rôle de <xref:System.Data.Linq.DataContext> est de traduire vos demandes d'objets en requêtes SQL sur la base de données, puis de rassembler les objets parmi les résultats.</span><span class="sxs-lookup"><span data-stu-id="5df12-107">The purpose of the <xref:System.Data.Linq.DataContext> is to translate your requests for objects into SQL queries to be made against the database, and then to assemble objects out of the results.</span></span> <span data-ttu-id="5df12-108">Le <xref:System.Data.Linq.DataContext> active [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] en implémentant le même modèle d’opérateur que les opérateurs de requête standard, tels que `Where` et `Select`.</span><span class="sxs-lookup"><span data-stu-id="5df12-108">The <xref:System.Data.Linq.DataContext> enables [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] by implementing the same operator pattern as the Standard Query Operators, such as `Where` and `Select`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5df12-109">Il est primordial de maintenir une connexion sécurisée.</span><span class="sxs-lookup"><span data-stu-id="5df12-109">Maintaining a secure connection is of the highest importance.</span></span> <span data-ttu-id="5df12-110">Pour plus d’informations, consultez [sécurité dans LINQ to SQL](security-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="5df12-110">For more information, see [Security in LINQ to SQL](security-in-linq-to-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df12-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="5df12-111">Example</span></span>  
 <span data-ttu-id="5df12-112">Dans l'exemple suivant, le <xref:System.Data.Linq.DataContext> est utilisé pour se connecter à l'exemple de base de données Northwind et récupérer des lignes de clients dont la ville est Londres.</span><span class="sxs-lookup"><span data-stu-id="5df12-112">In the following example, the <xref:System.Data.Linq.DataContext> is used to connect to the Northwind sample database and to retrieve rows of customers whose city is London.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#1)]
 [!code-vb[DLinqCommunicatingWithDatabase#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#1)]  
  
 <span data-ttu-id="5df12-113">Chaque table de base de données est représentée comme une collection `Table` disponible par le biais de la méthode <xref:System.Data.Linq.DataContext.GetTable%2A> en utilisant la classe d’entité pour l’identifier.</span><span class="sxs-lookup"><span data-stu-id="5df12-113">Each database table is represented as a `Table` collection available by way of the <xref:System.Data.Linq.DataContext.GetTable%2A> method, by using the entity class to identify it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5df12-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="5df12-114">Example</span></span>  
 <span data-ttu-id="5df12-115">Il est recommandé de déclarer un <xref:System.Data.Linq.DataContext> fortement typé au lieu de s'appuyer sur la classe <xref:System.Data.Linq.DataContext> de base et sur la méthode <xref:System.Data.Linq.DataContext.GetTable%2A>.</span><span class="sxs-lookup"><span data-stu-id="5df12-115">Best practice is to declare a strongly typed <xref:System.Data.Linq.DataContext> instead of relying on the basic <xref:System.Data.Linq.DataContext> class and the <xref:System.Data.Linq.DataContext.GetTable%2A> method.</span></span> <span data-ttu-id="5df12-116">Un <xref:System.Data.Linq.DataContext> fortement typé déclare toutes les collections `Table` comme membres du contexte, comme dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5df12-116">A strongly typed <xref:System.Data.Linq.DataContext> declares all `Table` collections as members of the context, as in the following example.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#2)]
 [!code-vb[DLinqCommunicatingWithDatabase#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#2)]  
  
 <span data-ttu-id="5df12-117">Vous pouvez exprimer ensuite plus simplement la requête de clients de Londres comme suit :</span><span class="sxs-lookup"><span data-stu-id="5df12-117">You can then express the query for customers from London more simply as:</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#5)]
 [!code-vb[DLinqCommunicatingWithDatabase#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5df12-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5df12-118">See also</span></span>

- [<span data-ttu-id="5df12-119">Communication avec la base de données</span><span class="sxs-lookup"><span data-stu-id="5df12-119">Communicating with the Database</span></span>](communicating-with-the-database.md)
