---
title: Comment utiliser des variables locales et des tableaux implicitement typés dans un guide de C# programmation d’expression de requête
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: f4ff71fc4dc1a0b2affa1f032ab1d3d6bb04d297
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705559"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Comment utiliser des variables locales et des tableaux implicitement typés dans une expression deC# requête (Guide de programmation)
Vous pouvez utiliser des variables locales implicitement typées chaque fois que vous voulez que le compilateur détermine le type d’une variable locale. Vous devez utiliser des variables locales implicitement typées pour stocker des types anonymes, qui sont souvent utilisés dans les expressions de requête. Les exemples suivants illustrent des utilisations facultatives et obligatoires de variables locales implicitement typées dans des requêtes.  
  
 Les variables locales implicitement typées sont déclarées à l’aide du mot clé contextuel [var](../../language-reference/keywords/var.md). Pour plus d’informations, consultez [Variables locales implicitement typées](./implicitly-typed-local-variables.md) et [Tableaux implicitement typés](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un scénario courant dans lequel le mot clé `var` est obligatoire : une expression de requête qui produit une séquence de types anonymes. Dans ce scénario, la variable de requête et la variable d’itération figurant dans l’instruction `foreach` doivent être implicitement typées avec `var`, car vous n’avez pas accès à un nom de type pour le type anonyme. Pour plus d’informations sur les types anonymes, consultez [Types anonymes](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le mot clé `var` est utilisé dans un cas similaire, à la différence que l’utilisation de `var` est facultative. Comme `student.LastName` est une chaîne, l’exécution de la requête retourne une séquence de chaînes. De ce fait, le type de `queryID` pourrait être déclaré en tant que `System.Collections.Generic.IEnumerable<string>` au lieu de `var`. Le mot clé `var` est utilisé pour des raisons pratiques. Dans l’exemple, la variable d’itération figurant dans l’instruction `foreach` est explicitement typée en tant que chaîne, mais elle aurait pu être déclarée à l’aide de `var`. Comme le type de la variable d’itération n’est pas un type anonyme, l’utilisation de `var` est facultative et non obligatoire. Pour rappel, `var` n’est pas en soi un type, mais une instruction indiquant au compilateur de déduire et d’assigner le type.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Méthodes d’extension](./extension-methods.md)
- [LINQ (Language Integrated Query)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ en C#](../../linq/index.md)
