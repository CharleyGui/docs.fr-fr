---
title: 'Procédure : Exécuter une requête qui retourne des résultats StructuralType'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
ms.openlocfilehash: 635fb20757f359520d292b850b2d554d4972aaab
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251457"
---
# <a name="how-to-execute-a-query-that-returns-structuraltype-results"></a><span data-ttu-id="444d4-102">Procédure : Exécuter une requête qui retourne des résultats StructuralType</span><span class="sxs-lookup"><span data-stu-id="444d4-102">How to: Execute a Query that Returns StructuralType Results</span></span>
<span data-ttu-id="444d4-103">Cette rubrique montre comment exécuter une commande par rapport à un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les résultats de <xref:System.Data.Metadata.Edm.StructuralType> en utilisant un objet <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="444d4-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.StructuralType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="444d4-104">Les classes <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> et <xref:System.Data.Metadata.Edm.ComplexType> sont dérivées de la classe <xref:System.Data.Metadata.Edm.StructuralType>.</span><span class="sxs-lookup"><span data-stu-id="444d4-104">The <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> and <xref:System.Data.Metadata.Edm.ComplexType> classes derive from the <xref:System.Data.Metadata.Edm.StructuralType> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="444d4-105">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="444d4-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="444d4-106">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]votre projet pour utiliser le.</span><span class="sxs-lookup"><span data-stu-id="444d4-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="444d4-107">Pour plus d’informations, consultez [Guide pratique pour Utilisez l’Assistant](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="444d4-107">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="444d4-108">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="444d4-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="444d4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="444d4-109">Example</span></span>  
 <span data-ttu-id="444d4-110">Cet exemple exécute une requête qui retourne des résultats <xref:System.Data.Metadata.Edm.EntityType>.</span><span class="sxs-lookup"><span data-stu-id="444d4-110">This example executes a query that returns <xref:System.Data.Metadata.Edm.EntityType> results.</span></span> <span data-ttu-id="444d4-111">Si vous transmettez la requête suivante en tant qu’argument à la fonction `ExecuteStructuralTypeQuery`, celle-ci affiche des détails sur l’objet `Products` :</span><span class="sxs-lookup"><span data-stu-id="444d4-111">If you pass the following query as an argument to the `ExecuteStructuralTypeQuery` function, the function displays details about the `Products`:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#selectproduct)]  
  
 <span data-ttu-id="444d4-112">Si vous transmettez une requête paramétrable, telle que la suivante, ajoutez les objets <xref:System.Data.EntityClient.EntityParameter> à la propriété <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> sur l'objet <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="444d4-112">If you pass a parameterized query, like the following, add the <xref:System.Data.EntityClient.EntityParameter> objects to the <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> property on the <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## <a name="see-also"></a><span data-ttu-id="444d4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="444d4-113">See also</span></span>

- [<span data-ttu-id="444d4-114">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="444d4-114">Entity SQL Reference</span></span>](./language-reference/entity-sql-reference.md)
- [<span data-ttu-id="444d4-115">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="444d4-115">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
