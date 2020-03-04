---
title: 'Comment : signer un assembly avec un nom fort'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160311"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Comment : signer un assembly avec un nom fort

> [!NOTE]
> Bien que .NET Core prenne en charge les assemblys avec nom fort et que tous les assemblys de la bibliothèque .NET Core soient signés, la majorité des assemblys tiers n’ont pas besoin de noms forts. Pour plus d’informations, consultez [signature avec nom fort](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) sur GitHub.

Il existe plusieurs façons de signer un assembly avec un nom fort :  
  
- À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio. Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.  
  
- À l’aide de l’outil [Assembly Linker (al. exe)](../../framework/tools/al-exe-assembly-linker.md) pour lier un module de code .NET Framework (un fichier *. netmodule* ) à un fichier de clé.  
  
- À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code. Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.  
  
- À l'aide des options du compilateur.  
  
 Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement. Pour plus d’informations sur la création d’une paire de clés, consultez [Comment : créer une paire de clés publique/privée](create-public-private-key-pair.md).  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Créer et signer un assembly avec un nom fort à l’aide de Visual Studio  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2. Choisissez l'onglet **Signature** .  
  
3. Sélectionnez la zone **Signer l'assembly** .  
  
4. Dans la zone **choisir un fichier de clé de nom fort** , choisissez **Parcourir**, puis naviguez jusqu’au fichier de clé. Pour créer un nouveau fichier de clé, choisissez **nouveau** et entrez son nom dans la boîte de dialogue **créer une clé de nom fort** .  
  
> [!NOTE]
> Pour [différer la signature d’un assembly](delay-sign.md), choisissez un fichier de clé publique.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Créer et signer un assembly avec un nom fort à l’aide de l’Assembly Linker  
  
À l' [invite de commandes développeur pour Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), entrez la commande suivante :  

**al** **/out :**\<*AssemblyName*> *\<moduleName >* **/keyfile :**\<*keyfilename*>  

Où :  

- *AssemblyName* est le nom de l’assembly fortement signé (un fichier *. dll* ou *. exe* ) que l’éditeur de liens d’assembly enverra.  
  
- *modulename* est le nom d’un module de code .NET Framework (un fichier *. netmodule* ) qui comprend un ou plusieurs types. Vous pouvez créer un fichier *. netmodule* en compilant votre code avec le commutateur C# `/target:module` ou Visual Basic.
  
- *keyfilename* est le nom du conteneur ou du fichier qui contient la paire de clés. Assembly Linker interprète un chemin d’accès relatif par rapport au répertoire actif.  

L’exemple suivant signe l’assembly *myAssembly. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Signer un assembly avec un nom fort à l’aide d’attributs  
  
1. Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.  

2. Compilez le fichier de code source normalement.  

   > [!NOTE]
   > Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source. Vous pouvez ignorer les avertissements.  

L’exemple suivant utilise l’attribut <xref:System.Reflection.AssemblyKeyFileAttribute> avec un fichier de clé appelé *keyfile. snk*, qui se trouve dans le répertoire où l’assembly est compilé.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source. Pour plus d’informations, consultez [Temporiser la signature d’un assembly](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Signer un assembly avec un nom fort à l’aide du compilateur  

Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++. Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé. Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.  

Pour plus d’informations sur la signature différée, consultez [temporisation d’un assembly](delay-sign.md).  

L’exemple suivant utilise le C# compilateur et signe l’assembly *utilitylibrary. dll* avec un nom fort à l’aide du fichier de clé *sgKey. snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
- [Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md)
- [Al.exe (Assembly Linker)](../../framework/tools/al-exe-assembly-linker.md)
- [Temporiser la signature d’un assembly](delay-sign.md)
- [Gérer la signature d’assemblys et de manifestes](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Signature, page du Concepteur de projets](/visualstudio/ide/reference/signing-page-project-designer)
