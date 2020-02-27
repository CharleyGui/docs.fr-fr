---
title: Implémentation d’interface explicite - Guide de programmation C#
ms.date: 01/24/2020
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: c6f1f849e0d4e831802b4c9b8b4bc3887363a34c
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628148"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a>Implémentation d’interface explicite (Guide de programmation C#)

Si une [classe](../../language-reference/keywords/class.md) implémente deux interfaces qui contiennent un membre avec la même signature, l’implémentation de ce membre sur la classe a pour conséquence que les deux interfaces utilisent ce membre comme leur implémentation. Dans l’exemple suivant, tous les appels à `Paint` appellent la même méthode. Ce premier exemple définit les types :

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefineTypes)]

L’exemple suivant appelle les méthodes :

[!code-csharp[DefineSimpleTypes](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallMethods)]

Lorsque deux membres d’interface n’exécutent pas la même fonction, il en résulte une implémentation incorrecte de l’une ou des deux interfaces. Il est possible d’implémenter un membre d’interface explicitement, en créant un membre de classe qui est appelé uniquement par le biais de l’interface, et est spécifique à cette interface. Nommez le membre de classe avec le nom de l’interface et un point. Par exemple :

[!code-csharp[DefineExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#ExplicitImplementation)]

Le membre de classe `IControl.Paint` est disponible uniquement via l’interface `IControl` et `ISurface.Paint` est disponible uniquement via `ISurface`. Les deux implémentations de méthode sont distinctes et ne sont pas directement disponibles sur la classe. Par exemple :

[!code-csharp[CallExplicitImplementation](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallExplicitImplementation)]

L’implémentation explicite est également utilisée pour résoudre les cas où deux interfaces déclarent chacune des membres différents du même nom, tels qu’une propriété et une méthode. Pour implémenter les deux interfaces, une classe doit utiliser l’implémentation explicite pour la propriété `P`, ou la méthode `P`, ou les deux, pour éviter une erreur du compilateur. Par exemple :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#NameCollision)]

Si une classe hérite d’une implémentation de méthode d’une interface, cette méthode est uniquement accessible par le biais d’une référence du type interface. Le membre hérité n’apparaît pas dans le cadre de l’interface publique. L’exemple suivant définit une implémentation par défaut pour une méthode d’interface :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#DefaultImplementation)]

L’exemple suivant appelle l’implémentation par défaut :

[!code-csharp[NameCollisions](~/samples/snippets/csharp/interfaces/ExplicitImplementation.cs#CallDefaultImplementation)]

Toute classe qui implémente l’interface `IControl` peut substituer la méthode `Paint` par défaut, en tant que méthode publique ou en tant qu’implémentation d’interface explicite.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](../classes-and-structs/index.md)
- [Interfaces](./index.md)
- [Héritage](../classes-and-structs/inheritance.md)
