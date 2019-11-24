---
title: 'How to: Build a multifile assembly'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: 0f8c6d57425657e321d80f9edffa20f27bc28770
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429558"
---
# <a name="how-to-build-a-multifile-assembly"></a>How to: Build a multifile assembly

Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.

> [!NOTE]
> L'IDE de Visual Studio pour C# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique. Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C++. Multifile assemblies are supported by .NET Framework only.

## <a name="create-a-multifile-assembly"></a>Create a multifile assembly

1. Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code. The default extension for code modules is *.netmodule*.

   Par exemple, supposons que le fichier `Stringer` a un espace de noms appelé `myStringer`, qui inclut une classe appelée `Stringer`. La classe `Stringer` contient une méthode appelée `StringerMethod` qui écrit une seule ligne dans la console.

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. Utilisez la commande suivante pour compiler ce code :

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   La spécification du paramètre *module* à l’aide de l’option du compilateur **/t:** indique que le fichier doit être compilé comme module et non comme assembly. The compiler produces a module called *Stringer.netmodule*, which can be added to an assembly.

3. Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code. Cette étape utilise l’option du compilateur **/addmodule**.

   In the following example, a code module called *Client* has an entry point `Main` method that references a method in the *Stringer.dll* module created in step 1.

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. Utilisez la commande suivante pour compiler ce code :

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   Spécifiez l’option **/t:module**, car ce module sera ajouté à un assembly lors d’une étape ultérieure. Specify the **/addmodule** option because the code in *Client* references a namespace created by the code in *Stringer.netmodule*. The compiler produces a module called *Client.netmodule* that contains a reference to another module, *Stringer.netmodule*.

   > [!NOTE]
   > Les compilateurs C# et Visual Basic prennent en charge la création directe d'assemblys multifichiers à l'aide de deux syntaxes différentes.
   >
   > Deux compilations créent un assembly à deux fichiers :
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > Une compilation crée un assembly à deux fichiers :
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. Utilisez l’utilitaire [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) pour créer le fichier de sortie qui contient le manifeste d’assembly. Ce fichier contient des informations sur les références de tous les modules ou ressources faisant partie de l'assembly.

    À l'invite de commandes, tapez la commande suivante :

    **al** \<*nom_module*> \<*nom_module*> … **/main:** \<*nom_méthode*>  **/out:** \<*nom_fichier*>  **/target:** \<*type_fichier_assembly*>

    Dans cette commande, les arguments *nom_module* spécifient le nom de chaque module à inclure dans l’assembly. L’option **/main:** spécifie le nom de la méthode représentant le point d’entrée de l’assembly. L’option **/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l’assembly. The **/target:** option specifies that the assembly is a console application executable ( *.exe*) file, a Windows executable ( *.win*) file, or a library ( *.lib*) file.

    In the following example, *Al.exe* creates an assembly that is a console application executable called *myAssembly.exe*. The application consists of two modules called *Client.netmodule* and *Stringer.netmodule*, and the executable file called *myAssembly.exe*, which contains only assembly metadata. The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in *Client.dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d’un assembly ou déterminer si un fichier est un assembly ou un module.

## <a name="see-also"></a>Voir aussi

- [Create assemblies](../../standard/assembly/create.md)
- [How to: View assembly contents](../../standard/assembly/view-contents.md)
- [Méthode de localisation des assemblys par le runtime](../deployment/how-the-runtime-locates-assemblies.md)
- [Multifile assemblies](multifile-assemblies.md)
