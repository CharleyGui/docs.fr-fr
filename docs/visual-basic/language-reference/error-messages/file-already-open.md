---
title: Le fichier est déjà ouvert.
ms.date: 07/20/2015
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
ms.openlocfilehash: 97f9e13e6802e793f7c7baf1f03ec51205eb6d42
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874172"
---
# <a name="file-already-open"></a><span data-ttu-id="75403-102">Le fichier est déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="75403-102">File already open</span></span>

<span data-ttu-id="75403-103">Parfois, un fichier doit être fermé avant une autre `FileOpen` opération ou une autre opération.</span><span class="sxs-lookup"><span data-stu-id="75403-103">Sometimes a file must be closed before another `FileOpen` or other operation can occur.</span></span> <span data-ttu-id="75403-104">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="75403-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="75403-105">Une `FileOpen` opération de mode de sortie séquentielle a été exécutée pour un fichier qui est déjà ouvert</span><span class="sxs-lookup"><span data-stu-id="75403-105">A sequential output mode `FileOpen` operation was executed for a file that is already open</span></span>  
  
- <span data-ttu-id="75403-106">Une instruction fait référence à un fichier ouvert.</span><span class="sxs-lookup"><span data-stu-id="75403-106">A statement refers to an open file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="75403-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="75403-107">To correct this error</span></span>  
  
1. <span data-ttu-id="75403-108">Fermez le fichier avant d’exécuter l’instruction.</span><span class="sxs-lookup"><span data-stu-id="75403-108">Close the file before executing the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75403-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75403-109">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
