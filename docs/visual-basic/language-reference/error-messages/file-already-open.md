---
title: Le fichier est déjà ouvert.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: ce8f8bf96d7355e45b2df82e8a131472c2ed2367
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162750"
---
# <a name="file-already-open"></a><span data-ttu-id="44ed8-102">Le fichier est déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="44ed8-102">File already open</span></span>

<span data-ttu-id="44ed8-103">Parfois, un fichier doit être fermé avant une autre `FileOpen` opération ou une autre opération.</span><span class="sxs-lookup"><span data-stu-id="44ed8-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="44ed8-104">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="44ed8-104">Among the possible causes of this error are:</span></span>

- <span data-ttu-id="44ed8-105">Une `FileOpen` opération de mode de sortie séquentielle a été exécutée pour un fichier qui est déjà ouvert</span><span class="sxs-lookup"><span data-stu-id="44ed8-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>

- <span data-ttu-id="44ed8-106">Une instruction fait référence à un fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="44ed8-106">A statement refers to an open file.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="44ed8-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="44ed8-107">To correct this error</span></span>

- <span data-ttu-id="44ed8-108">Fermez le fichier avant d’exécuter l’instruction.</span><span class="sxs-lookup"><span data-stu-id="44ed8-108">Close the file before executing the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="44ed8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44ed8-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
