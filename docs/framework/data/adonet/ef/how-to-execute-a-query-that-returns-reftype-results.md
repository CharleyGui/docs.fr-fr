---
title: 'Procédure : Exécuter une requête qui retourne des résultats RefType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dbbfbcd-93f5-4546-9dbf-e5fa290b69fa
ms.openlocfilehash: 1a7b5433ac514d22433dfb0bbf572a60854c1037
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251472"
---
# <a name="how-to-execute-a-query-that-returns-reftype-results"></a><span data-ttu-id="4cc86-102">Procédure : Exécuter une requête qui retourne des résultats RefType</span><span class="sxs-lookup"><span data-stu-id="4cc86-102">How to: Execute a Query that Returns RefType Results</span></span>
<span data-ttu-id="4cc86-103">Cette rubrique montre comment exécuter une commande par rapport à un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les résultats de <xref:System.Data.Metadata.Edm.RefType> en utilisant un objet <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="4cc86-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="4cc86-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="4cc86-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="4cc86-105">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]votre projet pour utiliser le.</span><span class="sxs-lookup"><span data-stu-id="4cc86-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="4cc86-106">Pour plus d'informations, voir [Procédure : Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="4cc86-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="4cc86-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="4cc86-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="4cc86-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cc86-108">Example</span></span>  
 <span data-ttu-id="4cc86-109">Cet exemple exécute une requête qui retourne des résultats <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="4cc86-109">This example executes a query that returns <xref:System.Data.Metadata.Edm.RefType> results.</span></span> <span data-ttu-id="4cc86-110">Si vous passez la requête suivante en tant qu’argument à la fonction `ExecuteRefTypeQuery`, celle-ci retourne une référence à l’entité :</span><span class="sxs-lookup"><span data-stu-id="4cc86-110">If you pass the following query as an argument to the `ExecuteRefTypeQuery` function, the function returns a reference to the entity:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF2](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref2)]  
  
 <span data-ttu-id="4cc86-111">Si vous transmettez une requête paramétrable, telle que la suivante, ajoutez les objets <xref:System.Data.EntityClient.EntityParameter> à la propriété <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> sur l'objet <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="4cc86-111">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#REF3](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#ref3)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlreftypes)]
 [!code-vb[DP EntityServices Concepts#eSQLRefTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlreftypes)]  
  
## <a name="see-also"></a><span data-ttu-id="4cc86-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cc86-112">See also</span></span>

- [<span data-ttu-id="4cc86-113">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4cc86-113">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4cc86-114">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4cc86-114">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
