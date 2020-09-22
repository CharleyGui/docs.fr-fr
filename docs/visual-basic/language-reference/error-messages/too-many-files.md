---
title: Trop de fichiers
ms.date: 07/20/2015
f1_keywords:
- vbrID67
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
ms.openlocfilehash: cd168ce86569d2d7558e21a5b4cc5ef385b28313
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873550"
---
# <a name="too-many-files"></a><span data-ttu-id="f66c4-102">Trop de fichiers</span><span class="sxs-lookup"><span data-stu-id="f66c4-102">Too many files</span></span>

<span data-ttu-id="f66c4-103">Soit des fichiers supplémentaires ont été créés dans le répertoire racine que le système d’exploitation le permet, soit des fichiers supplémentaires ont été ouverts que le nombre spécifié dans le paramètre **Files =** de votre fichier CONFIG.SYS.</span><span class="sxs-lookup"><span data-stu-id="f66c4-103">Either more files have been created in the root directory than the operating system permits, or more files have been opened than the number specified in the **files=** setting in your CONFIG.SYS file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f66c4-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f66c4-104">To correct this error</span></span>  
  
1. <span data-ttu-id="f66c4-105">Si votre programme ouvre, ferme ou enregistre des fichiers dans le répertoire racine, modifiez votre programme afin qu’il utilise un sous-répertoire.</span><span class="sxs-lookup"><span data-stu-id="f66c4-105">If your program is opening, closing, or saving files in the root directory, change your program so that it uses a subdirectory.</span></span>  
  
2. <span data-ttu-id="f66c4-106">Augmentez le nombre de fichiers spécifiés **dans votre fichier** de CONFIG.SYS, puis redémarrez votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f66c4-106">Increase the number of files specified in your **files=** setting in your CONFIG.SYS file, and restart your computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f66c4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f66c4-107">See also</span></span>

- [<span data-ttu-id="f66c4-108">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="f66c4-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
