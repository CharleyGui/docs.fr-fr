---
title: 'Comment: Créer des assemblées d’amis signés'
ms.date: 08/19/2019
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
dev_langs:
- csharp
- vb
ms.openlocfilehash: 9912fa70014a8828e994cf528644aaa7cb351fea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159492"
---
# <a name="how-to-create-signed-friend-assemblies"></a>Comment: Créer des assemblées d’amis signés
Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts. Les deux assemblys doivent avoir des noms forts. Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.  
  
## <a name="create-a-signed-assembly-and-a-friend-assembly"></a>Créer une assemblée signée et une assemblée d’amis  
  
1. Ouvrez une invite de commandes.  
  
2. Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique. Pour plus d’informations, voir [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md).  
  
    1. Générer une clé de nom fort pour cet exemple et le stocker dans le fichier *FriendAssemblies.snk*:  
  
         `sn -k FriendAssemblies.snk`  
  
    2. Extraire la clé publique de *FriendAssemblies.snk* et la mettre dans *FriendAssemblies.publickey*:  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3. Afficher la clé publique stockée dans le fichier *FriendAssemblies.publickey*:  
  
         `sn -tp FriendAssemblies.publickey`  
  
3. Créez un fichier de base visuelle ou C ou nommé *friend_signed_A* qui contient le code suivant. Le code <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> utilise l’attribut pour déclarer *friend_signed_B* comme un assemblage d’amis.  

   L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute. Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.  

   ```csharp  
   // friend_signed_A.cs  
   // Compile with:
   // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   using System.Runtime.CompilerServices;  

   [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
   class Class1  
   {  
       public void Test()  
       {  
           System.Console.WriteLine("Class1.Test");  
           System.Console.ReadLine();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_A.vb  
   ' Compile with:
   ' Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   Imports System.Runtime.CompilerServices  

   <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>
   Public Class Class1  
       Public Sub Test()  
           System.Console.WriteLine("Class1.Test")  
           System.Console.ReadLine()  
       End Sub  
   End Class  
   ```  

4. Compilez et *signez friend_signed_A* en utilisant la commande suivante.  

   ```csharp
   csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
   ```  

   ```vb
   Vbc -target:library -keyfile:FriendAssemblies.snk friend_signed_A.vb  
   ```  

5. Créez un fichier de base visuelle ou C ou nommé *friend_signed_B* qui contient le code suivant. Parce *que friend_signed_A* spécifie *friend_signed_B* comme un assemblage d’amis, le code en `Friend` *friend_signed_B* peut accéder à `internal` des types (C) ou (Visual Basic) et les membres de *friend_signed_A*. Le fichier contient le code suivant.  

   ```csharp  
   // friend_signed_B.cs  
   // Compile with:
   // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   public class Program  
   {  
       static void Main()  
       {  
           Class1 inst = new Class1();  
           inst.Test();  
       }  
   }  
   ```  

   ```vb  
   ' friend_signed_B.vb  
   ' Compile with:
   ' Vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   Module Sample  
       Public Sub Main()  
           Dim inst As New Class1  
           inst.Test()  
       End Sub  
   End Module  
   ```  

6. Compilez et *signez friend_signed_B* en utilisant la commande suivante.  

   ```csharp
   csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
   ```  

   ```vb
   vbc -keyfile:FriendAssemblies.snk -r:friend_signed_A.dll friend_signed_B.vb  
   ```  

   Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Vous devez spécifier explicitement le nom de l’assemblage de `-out` sortie (*.exe* ou *.dll*) en utilisant l’option compilateur. Pour plus d’informations, voir [-out (options de compilateur C)](../../csharp/language-reference/compiler-options/out-compiler-option.md) ou [-out (Visual Basic)](../../visual-basic/reference/command-line-compiler/out.md).  

7. Exécutez le fichier *friend_signed_B.exe.*  

   Le programme produit la chaîne **Class1.Test**.  
  
## <a name="net-security"></a>Sécurité .NET  
 Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. La principale différence <xref:System.Security.Permissions.StrongNameIdentityPermission> est que peut exiger des autorisations de <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> sécurité pour `internal` exécuter une section `Friend` particulière de code, tandis que l’attribut contrôle la visibilité des types et membres (C) ou (Visual Basic).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Assemblys dans .NET](index.md)
- [Assemblys friend](friend.md)
- [Comment : Créer des assemblées d’amis non signées](create-unsigned-friend.md)
- [-keyfile (C)](../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)
- [-keyfile (Visual Basic)](../../visual-basic/reference/command-line-compiler/keyfile.md)
- [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
