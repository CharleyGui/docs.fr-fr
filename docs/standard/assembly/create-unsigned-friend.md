---
title: 'Comment : créer des assemblys friend non signés'
description: Cet article montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés. Elle contient des informations sur la sécurité .NET.
ms.date: 08/19/2019
ms.assetid: 78cbc4f0-b021-4141-a4ff-eb4edbd814ca
dev_langs:
- csharp
- vb
ms.openlocfilehash: 8d3e13669c36048759fedeb3df1bfb59fd476317
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378968"
---
# <a name="how-to-create-unsigned-friend-assemblies"></a>Comment : créer des assemblys friend non signés

Cet exemple montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés.

## <a name="create-an-assembly-and-a-friend-assembly"></a>Créer un assembly et un assembly friend

1. Ouvrez une invite de commandes.

2. Créez un fichier C# ou Visual Basic nommé *friend_unsigned_A* qui contient le code suivant. Le code utilise l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut pour déclarer *friend_unsigned_B* comme un assembly friend.

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

3. Compilez et signez *friend_unsigned_A* à l’aide de la commande suivante :

   ```csharp
   csc /target:library friend_unsigned_A.cs
   ```

   ```vb
   vbc -target:library friend_unsigned_A.vb
   ```

4. Créez un fichier C# ou Visual Basic nommé *friend_unsigned_B* qui contient le code suivant. Étant donné que *friend_unsigned_A* spécifie *friend_unsigned_B* comme assembly friend, le code dans *friend_unsigned_B* peut accéder aux `internal` types et aux membres (C#) ou `Friend` (Visual Basic) à partir de *friend_unsigned_A*.

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

5. Compilez *friend_unsigned_B* à l’aide de la commande suivante.

   ```csharp
   csc /r:friend_unsigned_A.dll /out:friend_unsigned_B.exe friend_unsigned_B.cs
   ```

   ```vb
   vbc -r:friend_unsigned_A.dll friend_unsigned_B.vb
   ```

   Le nom de l’assembly qui est généré par le compilateur doit correspondre au nom de l’assembly friend qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Vous devez spécifier explicitement le nom de l’assembly de sortie (*. exe* ou *. dll*) à l’aide de l' `-out` option du compilateur. Pour plus d’informations, consultez [-out (options du compilateur C#)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).

6. Exécutez le fichier *friend_unsigned_B. exe* .

   Le programme génère deux chaînes : **Class1. test** et **Classe2. test**.

## <a name="net-security"></a>Sécurité .NET

Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, alors que l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribut contrôle la visibilité des `internal` `Friend` types et des membres (Visual Basic).

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblys dans .NET](index.md)
- [Assemblys friend](friend.md)
- [Comment : créer des assemblys friend signés](create-signed-friend.md)
- [Guide de programmation C#](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
