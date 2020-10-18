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
# <a name="bc30830-line-statements-are-no-longer-supported"></a><span data-ttu-id="eebfc-102">BC30830 : les instructions’line’ne sont plus prises en charge</span><span class="sxs-lookup"><span data-stu-id="eebfc-102">BC30830: 'Line' statements are no longer supported</span></span>

<span data-ttu-id="eebfc-103">Les instructions Line ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="eebfc-103">Line statements are no longer supported.</span></span> <span data-ttu-id="eebfc-104">La fonctionnalité d’e/s de fichier est disponible en tant que `Microsoft.VisualBasic.FileSystem.LineInput` et la fonctionnalité graphique est disponible sous la forme `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="eebfc-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>

 <span data-ttu-id="eebfc-105">**ID d’erreur :** BC30830</span><span class="sxs-lookup"><span data-stu-id="eebfc-105">**Error ID:** BC30830</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eebfc-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="eebfc-106">To correct this error</span></span>

- <span data-ttu-id="eebfc-107">Si vous effectuez un accès aux fichiers, utilisez `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="eebfc-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>

- <span data-ttu-id="eebfc-108">Pour des graphiques, utilisez `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="eebfc-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>

## <a name="see-also"></a><span data-ttu-id="eebfc-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eebfc-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="eebfc-110">Accès au fichier avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eebfc-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
