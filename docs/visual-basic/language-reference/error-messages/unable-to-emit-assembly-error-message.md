---
title: "Impossible de créer l'assembly : <error message>"
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 5776755a57fbc2b0086b1c9b6cfbb2f2b7eb03fa
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197276"
---
# <a name="unable-to-emit-assembly-error-message"></a>Impossible d’émettre l’assembly : \<message d’erreur >

Le compilateur Visual Basic appelle Assembly Linker (*al. exe*, également appelé ALink) pour générer un assembly avec un manifeste, et l’éditeur de liens signale une erreur lors de la phase d’émission de création de l’assembly.

**ID d’erreur :** BC30145

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message d’erreur cité et consultez la rubrique [al. exe](../../../framework/tools/al-exe-assembly-linker.md) pour obtenir plus d’explications et de conseils.

2. Essayez de signer l’assembly manuellement, à l’aide de [al. exe](../../../framework/tools/al-exe-assembly-linker.md) ou de [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.

### <a name="to-sign-the-assembly-manually"></a>Pour signer manuellement l'assembly

1. Utilisez [sn. exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)) pour créer un fichier de paire de clés publique/privée.

   Ce fichier a une extension *. snk* .

2. Supprimez la référence COM qui génère l'erreur de votre projet.

3. Ouvrez le [invite de commandes développeur pour Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   Dans Windows 10, entrez l' **invite de commandes développeur** dans la zone de recherche de la barre des tâches. Ensuite, sélectionnez **invite de commandes développeur pour VS 2017** dans la liste des résultats.

4. Remplacez le répertoire par le répertoire dans lequel vous souhaitez placer votre wrapper d’assembly.

5. Entrez la commande suivante :

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Voici un exemple de la commande réelle que vous pouvez entrer :

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Utilisez des guillemets doubles si un chemin d’accès ou un fichier contient des espaces.

6. Dans Visual Studio, ajoutez une référence d’assembly .NET au fichier que vous venez de créer.

## <a name="see-also"></a>Voir aussi

- [Al. exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (outil Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Guide pratique pour créer une paire de clés publique/privée](../../../standard/assembly/create-public-private-key-pair.md)
- [Nous contacter](/visualstudio/ide/feedback-options)
