---
title: Impossible d’obtenir un flux pour le journal
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 887356fac3abe5c9d28751f7c4d3b1908ed35acb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078383"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="ae6f2-102">Impossible d’obtenir un flux pour le journal</span><span class="sxs-lookup"><span data-stu-id="ae6f2-102">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="ae6f2-103">Impossible d’obtenir un flux pour le journal.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="ae6f2-104">Les noms de fichiers potentiels basés sur \<name> sont déjà utilisés.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ae6f2-105">La <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe n’a pas pu créer un nouveau fichier journal, car tous les noms de fichier journal potentiels basés sur \<name> sont déjà utilisés.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="ae6f2-106">Un nombre trop élevé de fichiers journaux peut indiquer un problème architectural avec l’application.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="ae6f2-107">Pour plus d’informations, consultez la documentation de la classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="ae6f2-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ae6f2-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ae6f2-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ae6f2-109">Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> la valeur <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> pour inclure un horodatage dans le nom du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="ae6f2-110">Archivez les journaux existants et supprimez-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.</span><span class="sxs-lookup"><span data-stu-id="ae6f2-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6f2-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae6f2-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="ae6f2-112">My. application. log</span><span class="sxs-lookup"><span data-stu-id="ae6f2-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="ae6f2-113">My. application. info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="ae6f2-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
