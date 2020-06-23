---
title: 'Procédure : Générer un assembly multifichier'
description: Découvrez comment créer (créer) un assembly multifichier dans .NET à l’aide d’un exemple de code pour illustrer chaque étape de la procédure.
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
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104954"
---
# <a name="how-to-build-a-multifile-assembly"></a>Procédure : Générer un assembly multifichier

Cet article explique comment créer un assembly multifichier et fournit le code illustrant chaque étape de la procédure.

> [!NOTE]
> L'IDE de Visual Studio pour C# et Visual Basic ne peut être utilisé que pour créer des assemblys à fichier unique. Si vous souhaitez créer des assemblys multifichiers, vous devez utiliser les compilateurs de ligne de commande ou Visual Studio avec Visual C++. Les assemblys multifichiers sont pris en charge par .NET Framework uniquement.

## <a name="create-a-multifile-assembly"></a>Créer un assembly multifichier

1. Compilez tous les fichiers contenant des espaces de noms référencés par d'autres modules de l'assembly dans des modules de code. L’extension par défaut pour les modules de code est *. netmodule*.

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

   La spécification du paramètre *module* à l’aide de l’option du compilateur **/t:** indique que le fichier doit être compilé comme module et non comme assembly. Le compilateur produit un module appelé *Stringer. netmodule*, qui peut être ajouté à un assembly.

3. Compilez tous les autres modules à l'aide des options du compilateur nécessaires pour indiquer les autres modules référencés dans le code. Cette étape utilise l’option du compilateur **/addmodule**.

   Dans l’exemple suivant, un module de code appelé *client* a une méthode de point d’entrée `Main` qui fait référence à une méthode dans le module *Stringer.dll* créé à l’étape 1.

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

   Spécifiez l’option **/t:module**, car ce module sera ajouté à un assembly lors d’une étape ultérieure. Spécifiez l’option **/addmodule** , car le code du *client* référence un espace de noms créé par le code dans *Stringer. netmodule*. Le compilateur produit un module appelé *client. netmodule* qui contient une référence à un autre module, *Stringer. netmodule*.

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

    Saisissez ensuite la commande suivante dans l’invite de commandes :

    **al** \<*module name*> \<*module name*>... **/main :** \<*method name*> **/out :** \<*file name*> **/target :**\<*assembly file type*>

    Dans cette commande, les arguments *nom_module* spécifient le nom de chaque module à inclure dans l’assembly. L’option **/main:** spécifie le nom de la méthode représentant le point d’entrée de l’assembly. L’option **/out:** spécifie le nom du fichier de sortie, qui contient les métadonnées de l’assembly. L’option **/target :** spécifie que l’assembly est un fichier exécutable (*. exe*) d’application console, un fichier exécutable Windows (*. Win*) ou un fichier de bibliothèque (*. lib*).

    Dans l’exemple suivant, *Al.exe* crée un assembly qui est un exécutable d’application console appelé *myAssembly.exe*. L’application se compose de deux modules appelés *client. netmodule* et *Stringer. netmodule*, et du fichier exécutable appelé *myAssembly.exe*, qui contient uniquement les métadonnées de l’assembly. Le point d’entrée de l’assembly est la `Main` méthode de la classe `MainClientApp` , qui se trouve dans *Client.dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Vous pouvez utiliser le [Désassembleur MSIL (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) pour examiner le contenu d’un assembly ou déterminer si un fichier est un assembly ou un module.

## <a name="see-also"></a>Voir aussi

- [Créer des assemblys](../../standard/assembly/create.md)
- [Comment : afficher le contenu d’un assembly](../../standard/assembly/view-contents.md)
- [Comment le runtime localise les assemblys](../deployment/how-the-runtime-locates-assemblies.md)
- [Assemblys multifichiers](multifile-assemblies.md)
