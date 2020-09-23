---
title: Impossible d’écrire dans le fichier journal, car la quantité d’espace disque libre deviendrait alors inférieure à la valeur ReservedSpace
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: e5247876c683812edf0eb73ab5f1a5e607b48102
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075601"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="45c38-102">Impossible d’écrire dans le fichier journal, car la quantité d’espace disque libre deviendrait alors inférieure à la valeur ReservedSpace</span><span class="sxs-lookup"><span data-stu-id="45c38-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>

<span data-ttu-id="45c38-103">La classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> n’a pas pu écrire dans le fichier journal pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="45c38-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="45c38-104">La quantité d’espace disque libre (en octets) est inférieure à la valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> .</span><span class="sxs-lookup"><span data-stu-id="45c38-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="45c38-105">—et—</span><span class="sxs-lookup"><span data-stu-id="45c38-105">—and—</span></span>  
  
- <span data-ttu-id="45c38-106">La valeur de la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> est <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="45c38-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45c38-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="45c38-107">To correct this error</span></span>  
  
1. <span data-ttu-id="45c38-108">Archivez les journaux existants et supprimez-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.</span><span class="sxs-lookup"><span data-stu-id="45c38-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="45c38-109">Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> une valeur inférieure pour réserver moins d’espace disque.</span><span class="sxs-lookup"><span data-stu-id="45c38-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="45c38-110">Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> la valeur <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> pour ignorer les messages indiquant une quantité d’espace disque libre insuffisante.</span><span class="sxs-lookup"><span data-stu-id="45c38-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c38-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45c38-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="45c38-112">My. application. log</span><span class="sxs-lookup"><span data-stu-id="45c38-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="45c38-113">My. application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="45c38-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
