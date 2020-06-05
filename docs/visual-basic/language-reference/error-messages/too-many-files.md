---
title: Trop de fichiers
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: 38d39ad20f350137d714ae5d09db5d2204b83621
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362798"
---
# <a name="too-many-files"></a><span data-ttu-id="45aad-102">Trop de fichiers</span><span class="sxs-lookup"><span data-stu-id="45aad-102">Too many files</span></span>
<span data-ttu-id="45aad-103">Soit des fichiers supplémentaires ont été créés dans le répertoire racine que le système d’exploitation le permet, soit des fichiers supplémentaires ont été ouverts que le nombre spécifié dans le paramètre **Files =** de votre configuration. Fichier SYS.</span><span class="sxs-lookup"><span data-stu-id="45aad-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45aad-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="45aad-104">To correct this error</span></span>  
  
1. <span data-ttu-id="45aad-105">Si votre programme ouvre, ferme ou enregistre des fichiers dans le répertoire racine, modifiez votre programme afin qu’il utilise un sous-répertoire.</span><span class="sxs-lookup"><span data-stu-id="45aad-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="45aad-106">Augmentez le nombre de fichiers spécifiés dans votre configuration de **fichiers =** . SYS, puis redémarrez votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="45aad-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45aad-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45aad-107">See also</span></span>

- [<span data-ttu-id="45aad-108">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="45aad-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
