---
title: 'Comment: Signer une assemblée avec un nom fort'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160311"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Comment: Signer une assemblée avec un nom fort

> [!NOTE]
> Bien que .NET Core soutienne des assemblées de nom fort, et que toutes les assemblées de la bibliothèque .NET Core soient signées, la majorité des assemblées tierces n’ont pas besoin de noms forts. Pour plus d’informations, voir [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) sur GitHub.

Il existe plusieurs façons de signer un assembly avec un nom fort :  
  
- À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio. Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.  
  
- En utilisant le [Linker d’assemblage (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) pour lier un module de code cadre .NET (un fichier *.netmodule)* avec un fichier clé.  
  
- À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code. Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.  
  
- À l'aide des options du compilateur.  
  
 Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement. Pour plus d’informations sur la création d’une paire de clés, voir [Comment : Créer une paire de clés public-privé.](create-public-private-key-pair.md)  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Créez et signez un assemblage avec un nom fort en utilisant Visual Studio  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2. Choisissez l'onglet **Signature** .  
  
3. Sélectionnez la zone **Signer l'assembly** .  
  
4. Dans la **boîte de fichier de fichier De nom fort,** choisissez **Browse,** puis naviguez vers le fichier clé. Pour créer un nouveau fichier clé, choisissez **New** et entrez son nom dans la boîte de dialogue **Create Strong Name Key.**  
  
> [!NOTE]
> Pour [différer la signature d’un assembly](delay-sign.md), choisissez un fichier de clé publique.  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Créer et signer une assemblée avec un nom fort en utilisant le Lien d’assemblage  
  
Au [Developer Command Prompt for Visual Studio,](../../framework/tools/developer-command-prompt-for-vs.md)entrez la commande suivante :  

**al** **/out:**\<*module assemblyNameName*> *\<>* **/keyfile:**\<*keyfileName*>  

Où :  

- *assemblyName* est le nom de l’assemblage fortement signé (un *fichier .dll* ou *.exe)* que l’Assemblée Linker émettra.  
  
- *moduleName* est le nom d’un module de code cadre .NET (un fichier *.netmodule)* qui comprend un ou plusieurs types. Vous pouvez créer un fichier *.netmodule* en `/target:module` compilant votre code avec le commutateur en C ou Visual Basic.
  
- *keyfileName* est le nom du conteneur ou du fichier qui contient la paire de clés. Assembly Linker interprète une voie relative par rapport à l’annuaire actuel.  

L’exemple suivant signe l’assemblage *MyAssembly.dll* avec un nom fort en utilisant le fichier clé *sgKey.snk*.  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Signez un assemblage avec un nom fort en utilisant des attributs  
  
1. Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.  

2. Compilez le fichier de code source normalement.  

   > [!NOTE]
   > Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source. Vous pouvez ignorer les avertissements.  

L’exemple suivant <xref:System.Reflection.AssemblyKeyFileAttribute> utilise l’attribut avec un fichier clé appelé *keyfile.snk*, qui est situé dans l’annuaire où l’assemblage est compilé.  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source. Pour plus d’informations, voir [Retard-signer une assemblée](delay-sign.md).  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Signez un assemblage avec un nom fort en utilisant le compilateur  

Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++. Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé. Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.  

Pour plus d’informations sur la signature des retards, voir [Retard-signer une assemblée](delay-sign.md).  

L’exemple suivant utilise le compilateur C et signe l’assemblage *UtilityLibrary.dll* avec un nom fort en utilisant le fichier clé *sgKey.snk*.  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>Voir aussi

- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
- [Guide pratique pour créer une paire de clés publique/privée](create-public-private-key-pair.md)
- [Al.exe (Assembly Linker)](../../framework/tools/al-exe-assembly-linker.md)
- [Temporiser la signature d’un assembly](delay-sign.md)
- [Gérer l’assemblage et la signature manifeste](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Page Signature, Concepteur de projet](/visualstudio/ide/reference/signing-page-project-designer)
