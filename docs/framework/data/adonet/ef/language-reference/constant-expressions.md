---
title: Expressions constantes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9d98a7be-b110-4edb-8eba-bed10f250b6d
ms.openlocfilehash: 163f73a7682d444214caa213751cb35f8f0e8743
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153038"
---
# <a name="constant-expressions"></a>Expressions constantes

Une expression constante est composée d'une valeur constante. Les valeurs constantes sont converties directement en expressions d’arborescence de commandes constantes, sans aucune traduction sur le client. Cela inclut les expressions qui génèrent une valeur constante. Par conséquent, le comportement de la source de données doit être prévu pour toutes les expressions impliquant des constantes. Il peut en résulter un comportement différent du comportement CLR.  
  
 L'exemple suivant illustre une expression constante qui est évaluée sur le serveur.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities ne prend pas en charge l’utilisation d’une classe d’utilisateur en tant que constante. Toutefois, une référence de propriété sur une classe d'utilisateur est considérée comme une constante. Elle est donc convertie en expression constante d'arborescence de commandes et exécutée sur la source de données.  
  
## <a name="see-also"></a>Voir aussi

- [Expressions dans les requêtes LINQ to Entities](expressions-in-linq-to-entities-queries.md)
