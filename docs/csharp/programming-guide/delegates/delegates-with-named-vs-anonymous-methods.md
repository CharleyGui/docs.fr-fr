---
title: Délégués avec des méthodes nommées vs anonymes - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712375"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Délégués avec méthodes nommées et méthodes anonymes (Guide de programmation C#)
Un [délégué](../../language-reference/builtin-types/reference-types.md) peut être associé à une méthode nommée. Quand vous instanciez un délégué à l’aide d’une méthode nommée, la méthode est passée en tant que paramètre, par exemple :  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 C’est ce qui s’appelle utiliser une méthode nommée. Les délégués construits avec une méthode nommée peuvent encapsuler une méthode [static](../../language-reference/keywords/static.md) ou une méthode d’instance. Les méthodes nommées représentent la seule façon d’instancier un délégué dans les versions précédentes de C#. Toutefois, dans une situation où la création d’une méthode constitue une charge de travail non souhaitée, C# vous permet d’instancier un délégué et de spécifier immédiatement un bloc de code que le délégué traite quand il est appelé. Le bloc peut contenir une expression lambda ou une méthode anonyme. Pour plus d’informations, consultez [Fonctions anonymes](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Notes   
 La méthode que vous passez en tant que paramètre de délégué doit avoir la même signature que la déclaration du délégué.  
  
 Une instance de délégué encapsule soit une méthode statique soit une méthode d’instance.  
  
 Même si le délégué peut utiliser un paramètre [out](../../language-reference/keywords/out-parameter-modifier.md), nous ne recommandons pas son utilisation avec les délégués d’événement multicast, car vous ne pouvez pas savoir quel délégué sera appelé.  
  
## <a name="example-1"></a>Exemple 1  
 L’exemple suivant est un exemple simple de déclaration et d’utilisation d’un délégué. Notez que le délégué, `Del`, et la méthode associée, `MultiplyNumbers`, ont la même signature  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Exemple 2  
 Dans l’exemple suivant, un délégué est associé à une méthode statique et à une méthode d’instance, et retourne des informations spécifiques à partir de chacune.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Délégués](./index.md)
- [Comment combiner les délégués (délégués multicast)](./how-to-combine-delegates-multicast-delegates.md)
- [Événements](../events/index.md)
