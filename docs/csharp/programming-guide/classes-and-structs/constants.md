---
title: Constantes - Guide de programmation C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 7da86a8999f6cc36a7b71f70fd92a363673824b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924531"
---
# <a name="constants-c-programming-guide"></a>Constantes (Guide de programmation C#)
Les constantes sont des valeurs immuables qui sont connues au moment de la compilation et qui ne changent pas pendant la durée de vie du programme. Les constantes sont déclarées avec le modificateur [const](../../language-reference/keywords/const.md). Seuls les types intégrés C# (à l’exclusion de <xref:System.Object?displayProperty=nameWithType>) peuvent être déclarés comme `const`. Pour obtenir une liste des types intégrés, consultez [Tableau des types intégrés](../../language-reference/keywords/built-in-types-table.md). Les types définis par l’utilisateur, notamment les classes, les structs et les tableaux, ne peuvent pas être `const`. Utilisez le modificateur [readonly](../../language-reference/keywords/readonly.md) pour créer une classe, un struct ou un tableau initialisé une fois au moment de l’exécution (par exemple, dans un constructeur) et qui ne peut pas être modifié ultérieurement.  
  
 C# ne prend pas en charge les propriétés, les événements ou les méthodes `const`.  
  
 Le type enum vous permet de définir des constantes nommées pour les types intégrés intégraux (par exemple, `int`, `uint`, `long`, etc.). Pour plus d’informations, consultez [enum](../../language-reference/keywords/enum.md).  
  
 Les constantes doivent être initialisées à mesure qu’elles sont déclarées. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 Dans cet exemple, la constante `months` est toujours 12, et ne peut pas être modifiée, même par la classe elle-même. En fait, quand le compilateur rencontre un identificateur constant dans du code source C# (par exemple, `months`), il substitue la valeur littérale directement dans le code en langage intermédiaire (IL, Intermediate Language) qu’il produit. Étant donné qu’aucune adresse de variable n’est associée à une constante au moment de l’exécution, les champs `const` ne peuvent pas être passés par référence et ne peuvent pas apparaître comme l-value dans une expression.  
  
> [!NOTE]
> Procédez avec précaution lorsque vous faites référence à des valeurs constantes définies dans un autre code telles que des DLL. Si une nouvelle version de la DLL définit une nouvelle valeur pour la constante, votre programme conserve l’ancienne valeur littérale jusqu’à ce qu’elle soit recompilée sur la nouvelle version.  
  
 Plusieurs constantes du même type peuvent être déclarées en même temps, par exemple :  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 L’expression utilisée pour initialiser une constante peut référencer une autre constante si elle ne crée pas de référence circulaire. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 Les constantes peuvent être marquées comme [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) ou [private protected](../../language-reference/keywords/private-protected.md). Ces modificateurs d’accès définissent la façon dont les utilisateurs de la classe peuvent accéder à la constante. Pour plus d’informations, consultez [Modificateurs d’accès](./access-modifiers.md).  
  
 Les constantes sont accessibles comme si elles étaient des champs [static](../../language-reference/keywords/static.md), car la valeur de la constante est identique pour toutes les instances du type. Vous n’utilisez pas le mot clé `static` pour les déclarer. Les expressions ne se trouvant pas dans la classe qui définit la constante doivent utiliser le nom de la classe, un point et le nom de la constante pour accéder à la constante. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Propriétés](./properties.md)
- [Types](../types/index.md)
- [readonly](../../language-reference/keywords/readonly.md)
- [Immuabilité dans C#, première partie : types d’immuabilité](https://blogs.msdn.microsoft.com/ericlippert/2007/11/13/immutability-in-c-part-one-kinds-of-immutability)
