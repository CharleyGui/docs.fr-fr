---
title: "Erreur lors de la création du manifeste d'assembly : <error message>"
ms.date: 07/20/2015
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
ms.openlocfilehash: a772167966c4ec858197cc2032f4ae3d4e86070c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163413"
---
# <a name="bc30140-error-creating-assembly-manifest-error-message"></a>BC30140 : erreur lors de la création du manifeste d’assembly : \<error message>

Le compilateur Visual Basic appelle Assembly Linker (Al.exe, également appelé ALink) pour générer un assembly avec un manifeste. L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.

 Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué. Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées. Pour différer la signature d’un assembly, vous devez cocher la case **Différer la signature uniquement** et fournir un fichier de clé valide contenant des informations de clés publiques. La clé privée n'est pas nécessaire quand la signature d'un assembly est différée. Pour plus d’informations, consultez [Procédure : signer l’assembly avec un nom fort](../../../standard/assembly/sign-strong-name.md).

 **ID d’erreur :** BC30140

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Examinez le message d’erreur cité et consultez la rubrique [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). pour obtenir une explication et des conseils supplémentaires sur l’erreur

2. Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.

## <a name="see-also"></a>Voir aussi

- [Comment : signer un assembly avec un nom fort](../../../standard/assembly/sign-strong-name.md)
- [Page Signature, Concepteur de projets](/visualstudio/ide/reference/signing-page-project-designer)
- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Nous contacter](/visualstudio/ide/feedback-options)
