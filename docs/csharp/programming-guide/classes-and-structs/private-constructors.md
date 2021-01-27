---
title: Constructeurs privés - Guide de programmation C#
description: Un constructeur privé est un constructeur d’instance spécial en C# utilisé pour limiter la manière dont un objet peut être créé. Elles peuvent être utilisées avec des méthodes de fabrique ou d’autres idiomes de construction.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899398"
---
# <a name="private-constructors-c-programming-guide"></a>Constructeurs privés (Guide de programmation C#)

Un constructeur privé est un constructeur d’instance spécial. Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques. Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe. Par exemple :  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 La déclaration du constructeur vide empêche la génération automatique d’un constructeur sans paramètre. Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut. En règle générale, le modificateur [private](../../language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.  
  
 Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe. Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique. Pour plus d’informations [, consultez classes statiques et membres de classe statique](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre une classe qui utilise un constructeur privé.  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Constructeurs privés](~/_csharplang/spec/classes.md#private-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Finaliseurs](./destructors.md)
- [priv](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
