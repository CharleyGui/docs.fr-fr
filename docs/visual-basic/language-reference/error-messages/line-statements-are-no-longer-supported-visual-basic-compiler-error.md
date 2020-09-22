---
title: Les instructions 'Line' ne sont plus prises en charge (erreur du compilateur Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 4ca1538dbde0d585b7b421d60cde4531c00e9145
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873829"
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
