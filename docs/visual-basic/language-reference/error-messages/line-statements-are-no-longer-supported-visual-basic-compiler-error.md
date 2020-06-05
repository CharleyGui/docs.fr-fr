---
title: Les instructions 'Line' ne sont plus prises en charge (erreur du compilateur Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397296"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Les instructions 'Line' ne sont plus prises en charge (erreur du compilateur Visual Basic)
Les instructions Line ne sont plus prises en charge. La fonctionnalité d’e/s de fichier est disponible en tant que `Microsoft.VisualBasic.FileSystem.LineInput` et la fonctionnalité graphique est disponible sous la forme `System.Drawing.Graphics.DrawLine` .  
  
 **ID d’erreur :** BC30830  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Si vous effectuez un accès aux fichiers, utilisez `Microsoft.VisualBasic.FileSystem.LineInput` .  
  
2. Pour des graphiques, utilisez `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO>
- <xref:System.Drawing>
- [Accès au fichier avec Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
