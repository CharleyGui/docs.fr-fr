---
title: Impossible d’écrire dans le fichier journal, car cette opération entraînerait un dépassement de la valeur MaximumSize
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 95a7b9036e7c1494cd44c250b0580bab5144417b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059455"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="f2b80-102">Impossible d’écrire dans le fichier journal, car cette opération entraînerait un dépassement de la valeur MaximumSize</span><span class="sxs-lookup"><span data-stu-id="f2b80-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>

<span data-ttu-id="f2b80-103">La classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> n’a pas pu écrire dans le fichier journal pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2b80-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="f2b80-104">La taille du fichier journal (en octets) est supérieure à la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="f2b80-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="f2b80-105">—et—</span><span class="sxs-lookup"><span data-stu-id="f2b80-105">—and—</span></span>  
  
- <span data-ttu-id="f2b80-106">La valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> est <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="f2b80-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f2b80-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f2b80-107">To correct this error</span></span>  
  
1. <span data-ttu-id="f2b80-108">Archivez les journaux existants et supprimez-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.</span><span class="sxs-lookup"><span data-stu-id="f2b80-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="f2b80-109">Modifiez la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> pour autoriser des tailles de journaux plus élevées.</span><span class="sxs-lookup"><span data-stu-id="f2b80-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="f2b80-110">Affectez la valeur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> à la propriété <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> pour ignorer les messages sans avertissement si le journal est trop volumineux.</span><span class="sxs-lookup"><span data-stu-id="f2b80-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b80-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b80-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="f2b80-112">My. application. log</span><span class="sxs-lookup"><span data-stu-id="f2b80-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="f2b80-113">My. application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="f2b80-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
