---
title: Les instructions 'Line' ne sont plus prises en charge (erreur du compilateur Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: f34095becf321c6cb4b316b6378a2da0107577ba
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162477"
---
# <a name="bc30830-line-statements-are-no-longer-supported"></a>BC30830 : les instructions’line’ne sont plus prises en charge

Les instructions Line ne sont plus prises en charge. La fonctionnalité d’e/s de fichier est disponible en tant que `Microsoft.VisualBasic.FileSystem.LineInput` et la fonctionnalité graphique est disponible sous la forme `System.Drawing.Graphics.DrawLine` .

 **ID d’erreur :** BC30830

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous effectuez un accès aux fichiers, utilisez `Microsoft.VisualBasic.FileSystem.LineInput` .

- Pour des graphiques, utilisez `System.Drawing.Graphics.Drawline`.

## <a name="see-also"></a>Voir aussi

- <xref:System.IO>
- <xref:System.Drawing>
- [Accès au fichier avec Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
