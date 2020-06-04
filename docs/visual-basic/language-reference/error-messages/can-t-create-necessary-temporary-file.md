---
title: Impossible de créer le fichier temporaire nécessaire
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: 1a1464e0ac0d87bf9763efe63f2e09927a157a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415425"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="f028e-102">Impossible de créer le fichier temporaire nécessaire</span><span class="sxs-lookup"><span data-stu-id="f028e-102">Can't create necessary temporary file</span></span>
<span data-ttu-id="f028e-103">Soit le lecteur est plein qui contient le répertoire spécifié par la variable d’environnement TEMP, soit la variable d’environnement TEMP spécifie un lecteur ou un répertoire non valide ou en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f028e-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f028e-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f028e-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f028e-105">Supprimez les fichiers du lecteur, s’ils sont pleins.</span><span class="sxs-lookup"><span data-stu-id="f028e-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="f028e-106">Spécifiez un autre lecteur dans la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="f028e-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="f028e-107">Spécifiez un lecteur valide pour la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="f028e-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="f028e-108">Supprimer la restriction en lecture seule du lecteur ou du répertoire actuellement spécifié.</span><span class="sxs-lookup"><span data-stu-id="f028e-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f028e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f028e-109">See also</span></span>

- [<span data-ttu-id="f028e-110">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="f028e-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
