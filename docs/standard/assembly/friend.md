---
title: Assemblys friend
description: Un assembly friend est un assembly .NET qui peut accéder aux types et aux membres internes d’un autre assembly (C#) ou Friend (Visual Basic).
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: 105621da2bd418c6294fa2bbec474809599cb6a5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378934"
---
# <a name="friend-assemblies"></a>Assemblys friend

Un *assembly friend* est un assembly qui peut accéder aux types et aux membres [internes](../../csharp/language-reference/keywords/internal.md) (C#) ou [Friend](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) d’un autre assembly. Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys. Ceci est particulièrement utile dans les scénarios suivants :

- Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.

- Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.

## <a name="remarks"></a>Remarks

Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné. L’exemple suivant utilise l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut dans l' *assembly A* et spécifie l’assembly *AssemblyB* comme assembly friend. Cela donne à l’assembly *AssemblyB* l’accès à tous les types et membres de l' *assembly A* qui sont marqués comme `internal` en C# ou `Friend` dans Visual Basic.

> [!NOTE]
> Quand vous compilez un assembly comme *AssemblyB* qui accède aux types internes ou aux membres internes d’un autre assembly comme *assembly A*, vous devez spécifier explicitement le nom du fichier de sortie (*. exe* ou *. dll*) à l’aide de l’option du compilateur **-out** . Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes. Pour plus d’informations, consultez [-out (C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

```csharp
using System.Runtime.CompilerServices;
using System;

[assembly: InternalsVisibleTo("AssemblyB")]

// The class is internal by default.
class FriendClass
{
    public void Test()
    {
        Console.WriteLine("Sample Class");
    }
}

// Public class that has an internal method.
public class ClassWithFriendMethod
{
    internal void Test()
    {
        Console.WriteLine("Sample Method");
    }

}
```

```vb
Imports System.Runtime.CompilerServices
<Assembly: InternalsVisibleTo("AssemblyB")>

' Friend class.
Friend Class FriendClass
    Public Sub Test()
        Console.WriteLine("Sample Class")
    End Sub
End Class

' Public class with a Friend method.
Public Class ClassWithFriendMethod
    Friend Sub Test()
        Console.WriteLine("Sample Method")
    End Sub
End Class
```

Seuls les assemblys que vous spécifiez explicitement comme Friends peuvent accéder aux `internal` types et aux membres (C#) ou `Friend` (Visual Basic). Par exemple, si *AssemblyB* est un Friend de *assembly a* et que *assembly c* fait référence à *AssemblyB*, l' *assembly c* n’a pas accès aux `internal` types (C#) ou `Friend` (Visual Basic) de l' *assembly a*.

Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Si l' *assembly A* déclare *AssemblyB* comme assembly friend, les règles de validation sont les suivantes :

- Si l' *assembly a porte un* nom fort, *AssemblyB* doit également avoir un nom fort. Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et de la clé publique de la clé de nom fort utilisée pour signer *AssemblyB*.

     Le nom de l’assembly friend qui est passé à l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut ne peut pas être le nom fort de *AssemblyB*. N’incluez pas la version, la culture, l’architecture ou le jeton de clé publique de l’assembly.

- Si l' *assembly a* n’A pas un nom fort, le nom de l’assembly friend doit se composer uniquement du nom de l’assembly. Pour plus d’informations, consultez [Comment : créer des assemblys friend non signés](create-unsigned-friend.md).

- Si *AssemblyB* a un nom fort, vous devez spécifier la clé de nom fort pour *AssemblyB* à l’aide du paramètre de projet ou de l' `/keyfile` option du compilateur de ligne de commande. Pour plus d’informations, consultez [Comment : créer des assemblys friend signés](create-signed-friend.md).

 La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :

- <xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.

- S’il existe des centaines de types dans l' *assembly A* que vous souhaitez partager avec *AssemblyB*, vous devez <xref:System.Security.Permissions.StrongNameIdentityPermission> les ajouter à tous. Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.

- Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics. Si vous utilisez un assembly friend, les types partagés sont déclarés en tant que `internal` (C#) ou `Friend` (Visual Basic).

Pour plus d’informations sur l’accès aux `internal` types et aux méthodes d’un assembly (c#) ou `Friend` (Visual Basic) à partir d’un fichier de module (fichier avec l’extension *. netmodule* ), consultez [-moduleassemblyname (C#)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Comment : créer des assemblys friend non signés](create-unsigned-friend.md)
- [Comment : créer des assemblys friend signés](create-signed-friend.md)
- [Assemblys dans .NET](index.md)
- [Guide de programmation C#](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
