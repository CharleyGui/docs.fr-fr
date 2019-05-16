---
title: "Impossible de créer l'assembly : <error message>"
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 012284aa42dfa29ad1a5e4ec4a4df5eaacbd4fb7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642276"
---
# <a name="unable-to-emit-assembly-error-message"></a>Impossible de créer l’assembly : \<message d’erreur >

Le compilateur Visual Basic appelle l’utilitaire Assembly Linker (*Al.exe*, également appelé Alink) pour générer un assembly avec un manifeste et l’éditeur de liens signale une erreur dans la phase d’émission de création de l’assembly.

**ID d’erreur :** BC30145

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message d’erreur cité et consultez la rubrique [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) pour obtenir davantage d’explications et de conseils.

2. Essayez de signer l’assembly manuellement, à l’aide la [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) ou [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.

### <a name="to-sign-the-assembly-manually"></a>Pour signer manuellement l'assembly

1. Utiliser le [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) pour créer un fichier de paire de clés publique/privée.

   Ce fichier a une *.snk* extension.

2. Supprimez la référence COM qui génère l'erreur de votre projet.

3. Ouvrez le [invite de commandes développeur pour Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   Dans Windows 10, entrez **invite de commandes développeur** dans la zone de recherche sur la barre des tâches. Ensuite, sélectionnez **invite de commandes développeur pour VS 2017** à partir de la liste des résultats.

4. Accédez au répertoire dans le répertoire où vous souhaitez placer le wrapper d’assembly.

5. Entrez la commande suivante :

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Est un exemple de la commande réelle, que vous pouvez entrer :

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Utilisez des guillemets si un fichier ou un chemin d’accès contient des espaces.

6. Dans Visual Studio, ajoutez une référence d’Assembly .NET au fichier que vous venez de créer.

## <a name="see-also"></a>Voir aussi

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (outil Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Guide pratique pour créer une paire de clés publique/privée](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Nous contacter](/visualstudio/ide/talk-to-us)
