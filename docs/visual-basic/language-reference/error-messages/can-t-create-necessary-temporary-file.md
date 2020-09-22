---
title: Impossible de créer le fichier temporaire nécessaire
ms.date: 07/20/2015
f1_keywords:
- vbrID322
ms.assetid: 53617b5b-eb06-4188-b4c2-8607cb9fbc79
ms.openlocfilehash: c6d8e471796a0fb745289df8b3d1b156265949ca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874672"
---
# <a name="cant-create-necessary-temporary-file"></a><span data-ttu-id="503ce-102">Impossible de créer le fichier temporaire nécessaire</span><span class="sxs-lookup"><span data-stu-id="503ce-102">Can't create necessary temporary file</span></span>

<span data-ttu-id="503ce-103">Soit le lecteur est plein qui contient le répertoire spécifié par la variable d’environnement TEMP, soit la variable d’environnement TEMP spécifie un lecteur ou un répertoire non valide ou en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="503ce-103">Either the drive is full that contains the directory specified by the TEMP environment variable, or the TEMP environment variable specifies an invalid or read-only drive or directory.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="503ce-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="503ce-104">To correct this error</span></span>  
  
1. <span data-ttu-id="503ce-105">Supprimez les fichiers du lecteur, s’ils sont pleins.</span><span class="sxs-lookup"><span data-stu-id="503ce-105">Delete files from the drive, if full.</span></span>  
  
2. <span data-ttu-id="503ce-106">Spécifiez un autre lecteur dans la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="503ce-106">Specify a different drive in the TEMP environment variable.</span></span>  
  
3. <span data-ttu-id="503ce-107">Spécifiez un lecteur valide pour la variable d’environnement TEMP.</span><span class="sxs-lookup"><span data-stu-id="503ce-107">Specify a valid drive for the TEMP environment variable.</span></span>  
  
4. <span data-ttu-id="503ce-108">Supprimer la restriction en lecture seule du lecteur ou du répertoire actuellement spécifié.</span><span class="sxs-lookup"><span data-stu-id="503ce-108">Remove the read-only restriction from the currently specified drive or directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503ce-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="503ce-109">See also</span></span>

- [<span data-ttu-id="503ce-110">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="503ce-110">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
