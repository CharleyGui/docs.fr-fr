---
title: 'Procédure : signer un assembly avec un nom fort'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927930"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>Procédure : signer un assembly avec un nom fort
Il existe plusieurs façons de signer un assembly avec un nom fort :  
  
- À l'aide de l'onglet **Signature** dans la boîte de dialogue **Propriétés** d'un projet dans Visual Studio. Il s'agit de la façon la plus facile et la plus pratique de signer un assembly avec un nom fort.  
  
- À l’aide de l’utilitaire [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour lier un module de code .NET Framework (un fichier .netmodule) à un fichier de clé.  
  
- À l'aide d'attributs d'assembly pour insérer les informations de nom fort dans votre code. Vous pouvez utiliser l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> , selon l'emplacement du fichier de clé à utiliser.  
  
- À l'aide des options du compilateur.  
  
 Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement. Pour plus d’informations sur la création d’une paire de clés, consultez [Guide pratique pour créer une paire de clés publique/privée](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>Pour créer et signer un assembly avec un nom fort à l'aide de Visual Studio  
  
1. Dans l’ **Explorateur de solutions**, ouvrez le menu contextuel du projet et choisissez **Propriétés**.  
  
2. Choisissez l'onglet **Signature** .  
  
3. Sélectionnez la zone **Signer l'assembly** .  
  
4. Dans la zone **Choisir un fichier de clé de nom fort**, choisissez **\<<Parcourir...>** , puis recherchez le fichier de clé. Pour créer un fichier de clé, choisissez **\<<Nouveau...>** et entrez son nom dans la boîte de dialogue **Créer une clé de nom fort**.  
  
> [!NOTE]
> Pour [différer la signature d’un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choisissez un fichier de clé publique.  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>Pour créer et signer un assembly avec un nom fort à l'aide de l'utilitaire Assembly Linker  
  
- À l’[Invite de commandes développeur pour Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), tapez la commande suivante :  
  
     **al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*>  
  
     où :  
  
     *assemblyName*  
     Nom de l'assembly fortement signé (un fichier .dll ou .exe) que l'utilitaire Assembly Linker émettra.  
  
     *moduleName*  
     Nom d’un module de code .NET Framework (un fichier .netmodule) qui inclut un ou plusieurs types. Vous pouvez créer un fichier .netmodule en compilant votre code avec le commutateur `/target:module` en C# ou Visual Basic.  
  
     *keyfileName*  
     Nom du conteneur ou du fichier qui contient la paire de clés. L'utilitaire Assembly Linker interprète un chemin d'accès relatif en relation avec le répertoire actif.  
  
 L'exemple suivant signe l'assembly `MyAssembly.dll` avec un nom fort à l'aide du fichier de clé `sgKey.snk`.  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 Pour plus d'informations sur l'utilisation de cet outil, consultez [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>Pour signer un assembly avec un nom fort à l'aide d'attributs  
  
1. Ajoutez l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> ou <xref:System.Reflection.AssemblyKeyNameAttribute> à votre fichier de code source et spécifiez le nom du fichier ou du conteneur qui contient la paire de clés à utiliser lors de la signature de l'assembly avec un nom fort.  
  
2. Compilez le fichier de code source normalement.  
  
> [!NOTE]
> Les compilateurs C# et Visual Basic génèrent des avertissements (CS1699 et BC41008, respectivement) lorsqu'ils rencontrent l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> ou <xref:System.Reflection.AssemblyKeyNameAttribute> dans le code source. Vous pouvez ignorer les avertissements.  
  
 L'exemple de code suivant utilise l'attribut <xref:System.Reflection.AssemblyKeyFileAttribute> avec un fichier de clé nommé `keyfile.snk`, situé dans le répertoire où l'assembly est compilé.  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 Vous pouvez également différer la signature d'un assembly lors de la compilation de votre fichier source. Pour plus d'informations, consultez [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>Pour signer un assembly avec un nom fort à l'aide du compilateur  
  
- Compilez vos fichiers de code source avec l'option du compilateur `/keyfile` ou `/delaysign` en C# et Visual Basic, ou l'option de l'éditeur de liens `/KEYFILE` ou `/DELAYSIGN` en C++. Après le nom de l'option, ajoutez une virgule et le nom du fichier de clé. Lorsque vous utilisez des compilateurs de ligne de commande, vous pouvez copier le fichier de clé dans le répertoire qui contient vos fichiers de code source.  
  
     Pour plus d’informations sur la signature différée, consultez [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).  
  
     L'exemple suivant utilise le compilateur C# et signe l'assembly `UtilityLibrary.dll` avec un nom fort à l'aide du fichier de clé `sgKey.snk`.  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [Guide pratique pour créer une paire de clés publique/privée](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [Gestion d’assembly et signature de manifeste](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [Page Signature, Concepteur de projet](/visualstudio/ide/reference/signing-page-project-designer)
