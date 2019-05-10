---
title: Expressions d'initialisation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 78bafcad0a0f34c74ea58f107621ad145c1b405b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631534"
---
# <a name="initialization-expressions"></a><span data-ttu-id="7d1ac-102">Expressions d'initialisation</span><span class="sxs-lookup"><span data-stu-id="7d1ac-102">Initialization Expressions</span></span>
<span data-ttu-id="7d1ac-103">Une expression d'initialisation initialise un nouvel objet.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="7d1ac-104">La plupart des expressions d'initialisation sont prises en charge, y compris la plupart des nouvelles expressions d'initialisation C# 3.0 et Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="7d1ac-105">Les types suivants peuvent être initialisés et retournés par une requête LINQ to Entities :</span><span class="sxs-lookup"><span data-stu-id="7d1ac-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="7d1ac-106">une collection de zéro, un ou plusieurs objets entité typés ou une projection de types complexes qui sont définis dans le modèle conceptuel ;</span><span class="sxs-lookup"><span data-stu-id="7d1ac-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="7d1ac-107">des types CLR pris en charge par [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ;</span><span class="sxs-lookup"><span data-stu-id="7d1ac-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="7d1ac-108">Collections inline.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-108">Inline collections.</span></span>  
  
- <span data-ttu-id="7d1ac-109">Types anonymes.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="7d1ac-110">L'initialisation de type anonyme est illustrée par l'exemple suivant dans la syntaxe d'expression de requête :</span><span class="sxs-lookup"><span data-stu-id="7d1ac-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="7d1ac-111">L'exemple suivant de syntaxe de requête fondée sur une méthode illustre l'initialisation de type anonyme :</span><span class="sxs-lookup"><span data-stu-id="7d1ac-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="7d1ac-112">L'initialisation de classe définie par l'utilisateur est également prise en charge.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="7d1ac-113">Le modèle d'initialisation C# 3.0 et Visual Basic 9.0 est pris en charge et suppose que l'accesseur Get et l'accesseur Set de propriété sont symétriques.</span><span class="sxs-lookup"><span data-stu-id="7d1ac-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="7d1ac-114">L'exemple suivant dans la syntaxe d'expression de requête illustre une classe personnalisée qui est initialisée dans la requête :</span><span class="sxs-lookup"><span data-stu-id="7d1ac-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="7d1ac-115">L'exemple suivant dans la syntaxe de requête fondée sur une méthode illustre une classe personnalisée qui est initialisée dans la requête :</span><span class="sxs-lookup"><span data-stu-id="7d1ac-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="7d1ac-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d1ac-116">See also</span></span>

- [<span data-ttu-id="7d1ac-117">Expressions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="7d1ac-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
