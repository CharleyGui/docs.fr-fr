---
title: 'Procédure : Exécuter une requête qui retourne des collections imbriquées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 3bf6e08e7842fbf235b519680b81f79fba4a7228
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198403"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="4b46b-102">Procédure : Exécuter une requête qui retourne des collections imbriquées</span><span class="sxs-lookup"><span data-stu-id="4b46b-102">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="4b46b-103">Cette rubrique indique comment exécuter une commande sur un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les collections imbriquées obtenues à l'aide d'un objet <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="4b46b-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="4b46b-104">Pour exécuter le code de cet exemple</span><span class="sxs-lookup"><span data-stu-id="4b46b-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="4b46b-105">Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4b46b-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="4b46b-106">Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b46b-106">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="4b46b-107">Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b46b-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="4b46b-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b46b-108">Example</span></span>  

 <span data-ttu-id="4b46b-109">Une *collection imbriquée* est une collection qui se trouve à l’intérieur d’une autre collection.</span><span class="sxs-lookup"><span data-stu-id="4b46b-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="4b46b-110">Le code suivant récupère une collection d’éléments `Contacts` et les collections imbriquées de `SalesOrderHeaders` qui sont associées à chaque élément `Contact`.</span><span class="sxs-lookup"><span data-stu-id="4b46b-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="4b46b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b46b-111">See also</span></span>

- [<span data-ttu-id="4b46b-112">Fournisseur EntityClient pour Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4b46b-112">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
