---
title: 'Procédure : Gérer une exception à l’aide de try-catch - Guide de programmation C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 5378de09962055fe7d2e100484ad69662c803e0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590236"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Procédure : Gérer une exception à l’aide de try/catch (Guide de programmation C#)
L’objectif d’un bloc [try-catch](../../language-reference/keywords/try-catch.md) est d’intercepter et de gérer une exception générée par du code opérationnel. Certaines exceptions peuvent être gérées dans un bloc `catch` et le problème résolu sans que l’exception soit levée à nouveau, mais le plus souvent la seule chose que vous puissiez faire est de vous assurer que l’exception appropriée est levée.  
  
## <a name="example"></a>Exemples  
 Dans cet exemple, <xref:System.IndexOutOfRangeException> n’est pas l’exception la plus appropriée : <xref:System.ArgumentOutOfRangeException> a de plus de sens pour la méthode car l’erreur est provoquée par l’argument `index` passé par l’appelant.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Commentaires  
 Le code qui provoque une exception est cloisonné dans le bloc `try`. Une instruction `catch` est ajoutée juste après pour gérer `IndexOutOfRangeException`, si elle se produit. Le bloc `catch` gère `IndexOutOfRangeException` et lève l’exception plus appropriée `ArgumentOutOfRangeException` à la place. Pour fournir à l’appelant autant d’informations que possible, pensez à spécifier l’exception d’origine comme <xref:System.Exception.InnerException%2A> de la nouvelle exception. Comme la propriété <xref:System.Exception.InnerException%2A> a la valeur [readonly](../../language-reference/keywords/readonly.md), vous devez l’affecter dans le constructeur de la nouvelle exception.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Exceptions et gestion des exceptions](./index.md)
- [Gestion des exceptions](./exception-handling.md)
