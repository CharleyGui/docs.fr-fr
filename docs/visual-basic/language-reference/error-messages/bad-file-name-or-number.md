---
title: Nom ou numéro de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: d57a9e78e6ae179d3050e5a92399ca731fa16ba7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874901"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="52e77-102">Nom ou numéro de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="52e77-102">Bad file name or number</span></span>

<span data-ttu-id="52e77-103">Une erreur s’est produite lors de la tentative d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="52e77-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="52e77-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="52e77-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="52e77-105">Une instruction fait référence à un fichier avec un nom ou un numéro de fichier qui n’a pas été spécifié dans l' `FileOpen` instruction ou qui a été spécifié dans une `FileOpen` instruction, mais qui a été fermé par la suite.</span><span class="sxs-lookup"><span data-stu-id="52e77-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="52e77-106">Une instruction fait référence à un fichier avec un nombre qui est en dehors de la plage de numéros de fichiers.</span><span class="sxs-lookup"><span data-stu-id="52e77-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="52e77-107">Une instruction fait référence à un nom de fichier ou à un nombre qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="52e77-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="52e77-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="52e77-108">To correct this error</span></span>  
  
1. <span data-ttu-id="52e77-109">Assurez-vous que le nom de fichier est spécifié dans une `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="52e77-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="52e77-110">Notez que si vous avez appelé l' `FileClose` instruction sans arguments, vous avez peut-être fermé par inadvertance tous les fichiers ouverts.</span><span class="sxs-lookup"><span data-stu-id="52e77-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="52e77-111">Si votre code génère des numéros de fichier algorithmiquement, assurez-vous que les nombres sont valides.</span><span class="sxs-lookup"><span data-stu-id="52e77-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="52e77-112">Vérifiez les noms de fichiers pour vous assurer qu’ils sont conformes aux conventions du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="52e77-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e77-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52e77-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="52e77-114">Conventions d'affectation de noms Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52e77-114">Visual Basic Naming Conventions</span></span>](../../programming-guide/program-structure/naming-conventions.md)
