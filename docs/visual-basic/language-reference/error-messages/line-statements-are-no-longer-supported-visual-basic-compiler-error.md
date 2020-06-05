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
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="aa583-102">Les instructions 'Line' ne sont plus prises en charge (erreur du compilateur Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa583-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="aa583-103">Les instructions Line ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="aa583-103">Line statements are no longer supported.</span></span> <span data-ttu-id="aa583-104">La fonctionnalité d’e/s de fichier est disponible en tant que `Microsoft.VisualBasic.FileSystem.LineInput` et la fonctionnalité graphique est disponible sous la forme `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="aa583-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="aa583-105">**ID d’erreur :** BC30830</span><span class="sxs-lookup"><span data-stu-id="aa583-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aa583-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="aa583-106">To correct this error</span></span>  
  
1. <span data-ttu-id="aa583-107">Si vous effectuez un accès aux fichiers, utilisez `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="aa583-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="aa583-108">Pour des graphiques, utilisez `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="aa583-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa583-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa583-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="aa583-110">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa583-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
