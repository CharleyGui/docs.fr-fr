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
# <a name="initialization-expressions"></a>Expressions d'initialisation
Une expression d'initialisation initialise un nouvel objet. La plupart des expressions d'initialisation sont prises en charge, y compris la plupart des nouvelles expressions d'initialisation C# 3.0 et Visual Basic 9.0. Les types suivants peuvent être initialisés et retournés par une requête LINQ to Entities :  
  
- une collection de zéro, un ou plusieurs objets entité typés ou une projection de types complexes qui sont définis dans le modèle conceptuel ;  
  
- des types CLR pris en charge par [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] ;  
  
- Collections inline.  
  
- Types anonymes.  
  
 L'initialisation de type anonyme est illustrée par l'exemple suivant dans la syntaxe d'expression de requête :  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 L'exemple suivant de syntaxe de requête fondée sur une méthode illustre l'initialisation de type anonyme :  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 L'initialisation de classe définie par l'utilisateur est également prise en charge. Le modèle d'initialisation C# 3.0 et Visual Basic 9.0 est pris en charge et suppose que l'accesseur Get et l'accesseur Set de propriété sont symétriques. L'exemple suivant dans la syntaxe d'expression de requête illustre une classe personnalisée qui est initialisée dans la requête :  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 L'exemple suivant dans la syntaxe de requête fondée sur une méthode illustre une classe personnalisée qui est initialisée dans la requête :  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions dans les requêtes LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
