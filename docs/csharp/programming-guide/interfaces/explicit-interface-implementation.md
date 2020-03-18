---
title: Implémentation d’interface explicite - Guide de programmation C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: ea32a279b7c464174a7fada5ef93ccf62ef39884
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167671"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implémentation d’interface explicite (Guide de programmation C#)

Si une [classe](../../language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation. Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode. Ce premier échantillon définit les types :

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

L’échantillon suivant appelle les méthodes :

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Lorsque deux membres de l’interface n’exécutent pas la même fonction, cela conduit à une implémentation incorrecte d’une ou des deux interfaces. Il est possible de mettre en œuvre explicitement un membre de l’interface, en créant un membre de classe qui n’est appelé que par l’interface, et qui est spécifique à cette interface. Nommez le membre de la classe avec le nom de l’interface et une période. Par exemple :

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`. Les deux implémentations de méthode sont séparées, et ni l’un ni l’autre ne sont disponibles directement sur la classe. Par exemple :

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

La mise en œuvre explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom tels qu’une propriété et une méthode. Pour implémenter les deux interfaces, une `P`classe doit `P`utiliser une implémentation explicite soit pour la propriété, ou la méthode, ou les deux, pour éviter une erreur de compilateur. Par exemple :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

En commençant par [C 8.0](../../whats-new/csharp-8.md#default-interface-methods), vous pouvez définir une implémentation pour les membres déclarés dans une interface. Si une classe hérite d’une implémentation de méthode à partir d’une interface, cette méthode n’est accessible que par une référence du type d’interface. Le membre hérité n’apparaît pas comme faisant partie de l’interface publique. L’échantillon suivant définit une implémentation par défaut pour une méthode d’interface :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

L’échantillon suivant invoque la mise en œuvre par défaut :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Toute classe qui `IControl` implémente l’interface peut passer outre à la méthode par défaut, `Paint` soit comme méthode publique, soit comme implémentation d’interface explicite.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Héritage](../classes-and-structs/inheritance.md)
