---
title: Erreur de chargement de la DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874383"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="238aa-102">Erreur de chargement de la DLL (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="238aa-102">Error in loading DLL (Visual Basic)</span></span>

<span data-ttu-id="238aa-103">Une bibliothèque de liens dynamiques (DLL) est une bibliothèque spécifiée dans la `Lib` clause d’une `Declare` instruction.</span><span class="sxs-lookup"><span data-stu-id="238aa-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="238aa-104">Les raisons possibles de cette erreur sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="238aa-104">Possible causes for this error include:</span></span>  
  
- <span data-ttu-id="238aa-105">Le fichier n’est pas un fichier exécutable DLL.</span><span class="sxs-lookup"><span data-stu-id="238aa-105">The file is not DLL executable.</span></span>  
  
- <span data-ttu-id="238aa-106">Le fichier n’est pas une DLL Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="238aa-106">The file is not a Microsoft Windows DLL.</span></span>  
  
- <span data-ttu-id="238aa-107">La DLL fait référence à une autre DLL qui n’est pas présente.</span><span class="sxs-lookup"><span data-stu-id="238aa-107">The DLL references another DLL that is not present.</span></span>  
  
- <span data-ttu-id="238aa-108">La DLL ou la DLL référencée ne se trouve pas dans un répertoire spécifié dans le chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="238aa-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="238aa-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="238aa-109">To correct this error</span></span>  
  
- <span data-ttu-id="238aa-110">Si le fichier est un fichier de texte source et qu’il n’est par conséquent pas un exécutable DLL, il doit être compilé et lié à un formulaire exécutable DLL.</span><span class="sxs-lookup"><span data-stu-id="238aa-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
- <span data-ttu-id="238aa-111">Si le fichier n’est pas une DLL Microsoft Windows, obtenez l’équivalent Microsoft Windows.</span><span class="sxs-lookup"><span data-stu-id="238aa-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
- <span data-ttu-id="238aa-112">Si la DLL fait référence à une autre DLL qui n’est pas présente, obtenez la DLL référencée et rendez-la disponible.</span><span class="sxs-lookup"><span data-stu-id="238aa-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
- <span data-ttu-id="238aa-113">Si la dll ou la DLL référencée ne se trouve pas dans un répertoire spécifié par le chemin d’accès, déplacez la DLL vers un répertoire référencé.</span><span class="sxs-lookup"><span data-stu-id="238aa-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="238aa-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="238aa-114">See also</span></span>

- [<span data-ttu-id="238aa-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="238aa-115">Declare Statement</span></span>](../statements/declare-statement.md)
