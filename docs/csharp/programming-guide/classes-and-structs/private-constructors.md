---
title: Constructeurs privés - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705442"
---
# <a name="private-constructors-c-programming-guide"></a>Constructeurs privés (Guide de programmation C#)
Un constructeur privé est un constructeur d’instance spécial. Il est généralement utilisé dans les classes qui contiennent uniquement des membres statiques. Si une classe a un ou plusieurs constructeurs privés, mais n’a aucun constructeur public, les autres classes (à l’exception des classes imbriquées) ne peuvent pas créer d’instances de cette classe. Par exemple :  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 La déclaration du constructeur vide empêche la génération automatique d’un constructeur sans paramètre. Notez que si vous n’utilisez pas de modificateur d’accès avec le constructeur, le constructeur est toujours privé par défaut. En règle générale, le modificateur [private](../../language-reference/keywords/private.md) est explicitement utilisé pour spécifier que la classe ne peut pas être instanciée.  
  
 Les constructeurs privés servent à empêcher la création d’instances d’une classe quand il n’y a pas de champs ou de méthodes d’instance (par exemple, la classe <xref:System.Math>) ou quand une méthode est appelée pour obtenir une instance d’une classe. Si toutes les méthodes dans la classe sont statiques, définissez la classe entière comme statique. Pour plus d’informations, consultez [les classes statiques et les membres de la classe statique](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a> Exemple  
 L’exemple suivant montre une classe qui utilise un constructeur privé.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Notez que si vous décommentez l’instruction suivante dans l’exemple, une erreur est générée, car le constructeur a un niveau de protection qui le rend inaccessible :  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Constructeurs privés](~/_csharplang/spec/classes.md#private-constructors) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Constructeurs](./constructors.md)
- [Finaliseurs](./destructors.md)
- [Privé](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)
