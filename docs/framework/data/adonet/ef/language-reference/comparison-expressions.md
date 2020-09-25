---
title: Expressions de comparaison
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d92020f353393eee683e578f4306cd4a2f214152
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197844"
---
# <a name="comparison-expressions"></a>Expressions de comparaison

Une expression de comparaison définit une valeur constante, une valeur de propriété ou un résultat de méthode par rapport à une autre valeur (égal, différent de, supérieur à ou inférieur à). Si une comparaison particulière n’est pas valide pour LINQ to Entities, une exception est levée. Toutes les comparaisons, implicites et explicites, requièrent que tous les composants soient comparables dans la source de données. Des expressions de comparaison sont souvent utilisées dans des clauses `Where` pour restreindre les résultats d'une requête.  
  
 L'exemple suivant dans la syntaxe d'expression de requête présente une requête qui retourne des résultats dans lesquels le numéro de commande client est égal à SO43663 :  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 L'exemple suivant dans la syntaxe de requête fondée sur une méthode présente une requête qui retourne des résultats dans lesquels le numéro de commande client est égal à SO43663 :  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 L'exemple suivant dans la syntaxe d'expression de requête présente une requête qui retourne des informations de commande client dans lesquelles la date d'expédition est égale au 8 juillet 2001 :  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 L'exemple suivant dans la syntaxe de requête fondée sur une méthode présente une requête qui retourne des informations de commande client dans lesquelles la date d'expédition est égale au 8 juillet 2001 :  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Les expressions qui génèrent une constante sont converties au niveau du serveur, et aucune tentative d'évaluation locale n'est effectuée. L'exemple suivant utilise une expression dans la clause `Where` qui génère une constante.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities ne prend pas en charge l’utilisation d’une classe d’utilisateur en tant que constante. Toutefois, une référence de propriété sur une classe d'utilisateur est considérée comme une constante. Elle est donc convertie en expression constante d'arborescence de commandes et exécutée sur la source de données.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Les méthodes qui retournent une expression constante ne sont pas prises en charge. L'exemple suivant contient une méthode dans la clause `Where` qui retourne une constante. Cet exemple lève une exception au moment de l'exécution.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Voir aussi

- [Expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md)
