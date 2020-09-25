---
title: 'Procédure : Exécuter une requête paramétrable Entity SQL avec EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: d66b77553e677c42ccedf7e66bf4f5763db92fa4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192228"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="75ee0-102">Procédure : Exécuter une requête paramétrable Entity SQL avec EntityCommand</span><span class="sxs-lookup"><span data-stu-id="75ee0-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>

<span data-ttu-id="75ee0-103">Cette rubrique montre comment exécuter une [!INCLUDE[esql](../../../../../includes/esql-md.md)] requête qui a des paramètres à l’aide d’un <xref:System.Data.EntityClient.EntityCommand> objet.</span><span class="sxs-lookup"><span data-stu-id="75ee0-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="75ee0-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="75ee0-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="75ee0-105">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="75ee0-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="75ee0-106">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="75ee0-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="75ee0-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="75ee0-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="75ee0-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="75ee0-108">Example</span></span>  

 <span data-ttu-id="75ee0-109">L'exemple suivant montre comment construire une chaîne de requête comportant deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="75ee0-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="75ee0-110">Il crée ensuite un objet <xref:System.Data.EntityClient.EntityCommand>, ajoute deux paramètres à la collection <xref:System.Data.EntityClient.EntityParameter> de cet objet <xref:System.Data.EntityClient.EntityCommand>, puis itère au sein de la collection d’éléments `Contact`.</span><span class="sxs-lookup"><span data-stu-id="75ee0-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="75ee0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75ee0-111">See also</span></span>

- <span data-ttu-id="75ee0-112">[Comment : exécuter une requête paramétrée](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="75ee0-112">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="75ee0-113">Langage d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="75ee0-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
