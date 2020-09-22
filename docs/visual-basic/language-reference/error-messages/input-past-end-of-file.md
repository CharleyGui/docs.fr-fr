---
title: L'entrée dépasse la fin du fichier
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: c0cb0373fb0652e9600ac8651661708414561aca
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873964"
---
# <a name="input-past-end-of-file"></a><span data-ttu-id="c6c5b-102">L'entrée dépasse la fin du fichier</span><span class="sxs-lookup"><span data-stu-id="c6c5b-102">Input past end of file</span></span>

<span data-ttu-id="c6c5b-103">Soit une `Input` instruction lit à partir d’un fichier vide, soit une instruction dans laquelle toutes les données sont utilisées, ou vous avez utilisé la `EOF` fonction avec un fichier ouvert pour un accès binaire.</span><span class="sxs-lookup"><span data-stu-id="c6c5b-103">Either an `Input` statement is reading from a file that is empty or one in which all the data is used, or you used the `EOF` function with a file opened for binary access.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6c5b-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c6c5b-104">To correct this error</span></span>  
  
1. <span data-ttu-id="c6c5b-105">Utilisez la `EOF` fonction immédiatement avant l' `Input` instruction pour détecter la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="c6c5b-105">Use the `EOF` function immediately before the `Input` statement to detect the end of the file.</span></span>  
  
2. <span data-ttu-id="c6c5b-106">Si le fichier est ouvert pour un accès binaire, utilisez `Seek` et `Loc` .</span><span class="sxs-lookup"><span data-stu-id="c6c5b-106">If the file is opened for binary access, use `Seek` and `Loc`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c5b-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6c5b-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
