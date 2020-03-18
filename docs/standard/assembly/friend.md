---
title: Assemblys friend
ms.date: 08/20/2019
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
dev_langs:
- csharp
- vb
ms.openlocfilehash: a74d4b74ead8492028a092e090f9281231802a87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348175"
---
# <a name="friend-assemblies"></a>Assemblys friend

Une *assemblée d’amis* est une assemblée qui peut accéder aux types [internes](../../csharp/language-reference/keywords/internal.md) d’une autre assemblée (C) ou [Ami](../../visual-basic/language-reference/modifiers/friend.md) (Visual Basic) et aux membres. Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys. Ceci est particulièrement utile dans les scénarios suivants :

- Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.

- Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal` en C# ou `Friend` en Visual Basic.

## <a name="remarks"></a>Notes 

Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné. L’exemple suivant <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> utilise l’attribut dans *l’Assemblée A* et spécifie *l’assemblage AssemblyB* comme une assemblée d’amis. Cela donne à *l’Assemblée AssemblyB* l’accès à `internal` tous les `Friend` types et membres de *l’Assemblée A* qui sont marqués comme dans C ou dans Visual Basic.

> [!NOTE]
> Lorsque vous compilez une assemblée comme *AssemblyB* qui accédera aux types internes ou aux membres internes d’une autre assemblée comme *l’Assemblée A*, vous devez spécifier explicitement le nom du fichier de sortie (*.exe* ou *.dll*) en utilisant l’option de compilateur-out. **-out** Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes. Pour plus d’informations, voir [-out (C)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

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

Seuls les assemblages que vous `internal` spécifiez `Friend` explicitement en tant qu’amis peuvent accéder aux types et aux membres (de base visuelle). Par exemple, si *AssemblyB* est un ami de *l’Assemblée A* et *de l’Assemblée C* références *AssemblyB*, *l’Assemblée C* n’a pas accès aux `internal` types (C) ou `Friend` (Visual Basic) à *l’Assemblée A*.

Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Si *l’Assemblée A* déclare *AssemblyB* comme assemblée d’amis, les règles de validation sont les suivantes :

- Si *l’Assemblée A* est forte nommée, *AssemblyB* doit également être forte nommée. Le nom de l’assemblée d’amis qui est transmis à l’attribut doit se composer du nom de l’assemblée et de la clé publique de la clé de nom fort qui est utilisé pour signer *AssemblyB*.

     Le nom d’assemblée d’ami qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ne peut pas être le nom fort de *AssemblyB*. N’incluez pas la version d’assemblage, la culture, l’architecture ou le jeton de clé publique.

- Si *l’Assemblée A* n’est pas forte nommée, le nom d’assemblage d’ami ne doit se composer que du nom de l’assemblée. Pour plus d’informations, voir [Comment : Créer des assemblées d’amis non signées.](create-unsigned-friend.md)

- Si *AssemblyB* est nommé fort, vous devez spécifier la clé de nom `/keyfile` fort pour *AssemblyB* en utilisant le paramètre de projet ou l’option de compilateur de ligne de commande. Pour plus d’informations, voir [Comment : Créer des assemblées d’amis signées.](create-signed-friend.md)

 La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :

- <xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.

- S’il y a des centaines de types à *l’Assemblée* <xref:System.Security.Permissions.StrongNameIdentityPermission> A que vous voulez partager avec *AssemblyB,* vous devez les ajouter à tous. Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.

- Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics. Si vous utilisez un assemblage d’amis, les types partagés sont déclarés comme `internal` (C) ou `Friend` (Visual Basic).

Pour plus d’informations sur `internal` la façon d’accéder aux types et méthodes `Friend` d’une assemblée (C) ou (Visual Basic) à partir d’un fichier module (un fichier avec l’extension *.netmodule),* [voir-moduleassemblyname (C)](../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md) ou [-moduleassemblyname (Visual Basic)](../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- <xref:System.Security.Permissions.StrongNameIdentityPermission>
- [Comment : Créer des assemblées d’amis non signées](create-unsigned-friend.md)
- [Comment: Créer des assemblées d’amis signés](create-signed-friend.md)
- [Assemblys dans .NET](index.md)
- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
