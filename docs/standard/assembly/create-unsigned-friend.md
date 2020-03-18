---
title: 'Comment : Créer des assemblées d’amis non signées'
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: f8fec064507553b8208083578165965de2303a33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352435"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Comment : Créer des assemblées d’amis non signées

Cet exemple montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Créer une assemblée et une assemblée d’amis

1. Ouvrez une invite de commandes.

2. Créez un fichier de base visuelle ou C ou nommé *friend_unsigned_A* qui contient le code suivant. Le code <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> utilise l’attribut pour déclarer *friend_unsigned_B* comme un assemblage d’amis.

   ```csharp
   // friend_unsigned_A.cs
   // Compile with:
   // csc /target:library friend_unsigned_A.cs
   using System.Runtime.CompilerServices;
   using System;

   [assembly: InternalsVisibleTo("friend_unsigned_B")]

   // Type is internal by default.
   class Class1
   {
       public void Test()
       {
           Console.WriteLine("Class1.Test");
       }
   }

   // Public type with internal member.
   public class Class2
   {
       internal void Test()
       {
           Console.WriteLine("Class2.Test");
       }
   }
   ```

   ```vb
   ' friend_unsigned_A.vb
   ' Compile with:
   ' vbc -target:library friend_unsigned_A.vb
   Imports System.Runtime.CompilerServices

   <Assembly: InternalsVisibleTo("friend_unsigned_B")>

   ' Friend type.
   Friend Class Class1
       Public Sub Test()
           Console.WriteLine("Class1.Test")
       End Sub
   End Class

   ' Public type with Friend member.
   Public Class Class2
       Friend Sub Test()
           Console.WriteLine("Class2.Test")
       End Sub
   End Class
   ```

3. Compilez et *signez friend_unsigned_A* en utilisant la commande suivante :

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Créez un fichier de base visuelle ou C ou nommé *friend_unsigned_B* qui contient le code suivant. Parce *que friend_unsigned_A* spécifie *friend_unsigned_B* comme un assemblage d’amis, le code en `Friend` *friend_unsigned_B* peut accéder à `internal` des types (C) ou (Visual Basic) et les membres de *friend_unsigned_A*.

   ```csharp
   // friend_unsigned_B.cs
   // Compile with:
   // csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   public class Program
   {
       static void Main()
       {
           // Access an internal type.
           Class1 inst1 = new Class1();
           inst1.Test();

           Class2 inst2 = new Class2();
           // Access an internal member of a public type.
           inst2.Test();

           System.Console.ReadLine();
       }
   }
   ```

   ```vb
   ' friend_unsigned_B.vb
   ' Compile with:
   ' vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   Module Module1
       Sub Main()
           ' Access a Friend type.
           Dim inst1 As New Class1()
           inst1.Test()

           Dim inst2 As New Class2()
           ' Access a Friend member of a public type.
           inst2.Test()

           System.Console.ReadLine()
       End Sub
   End Module
   ```

5. Compiler *friend_unsigned_B* en utilisant la commande suivante.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Le nom de l’assembly qui est généré par le compilateur doit correspondre au nom de l’assembly friend qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Vous devez spécifier explicitement le nom de l’assemblage de `-out` sortie (*.exe* ou *.dll*) en utilisant l’option compilateur. Pour plus d’informations, voir [-out (options de compilateur C)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md)..

6. Exécutez le fichier *friend_unsigned_B.exe.*

   Le programme produit deux chaînes : **Class1.Test** et **Class2.Test**.

## <a name="net-security"></a>Sécurité .NET

Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. La principale différence <xref:System.Security.Permissions.StrongNameIdentityPermission> est que peut exiger des autorisations de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> sécurité pour `internal` exécuter `Friend` une section particulière de code, tandis que l’attribut contrôle la visibilité ou (Visual Basic) types et les membres.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblys dans .NET](index.md)
- [Assemblys friend](friend.md)
- [Comment: Créer des assemblées d’amis signés](create-signed-friend.md)
- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
