---
title: Nom ou numéro de fichier incorrect
ms.date: 07/20/2015
f1_keywords:
- vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
ms.openlocfilehash: 7a16e951030731bdcbb48b5fbb1a0d1881d5e1ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619390"
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="ce4fd-102">Nom ou numéro de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="ce4fd-102">Bad file name or number</span></span>
<span data-ttu-id="ce4fd-103">Une erreur s’est produite lors de la tentative d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="ce4fd-104">Parmi les causes possibles de cette erreur sont :</span><span class="sxs-lookup"><span data-stu-id="ce4fd-104">Among the possible causes for this error are:</span></span>  
  
- <span data-ttu-id="ce4fd-105">Une instruction fait référence à un fichier avec un nom de fichier ou d’un nombre qui n’a pas été spécifié dans le `FileOpen` instruction ou qui a été spécifié dans un `FileOpen` instruction mais elle était par la suite fermé.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
- <span data-ttu-id="ce4fd-106">Une instruction fait référence à un fichier avec un nombre qui est en dehors de la plage de numéros de fichier.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
- <span data-ttu-id="ce4fd-107">Une instruction fait référence à un nom de fichier ou un nombre qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce4fd-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="ce4fd-108">To correct this error</span></span>  
  
1. <span data-ttu-id="ce4fd-109">Assurez-vous que le nom de fichier est spécifié dans un `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="ce4fd-110">Notez que si vous avez appelé la `FileClose` instruction sans arguments, vous avez peut-être fermé accidentellement tous les fichiers ouverts.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2. <span data-ttu-id="ce4fd-111">Si votre code génère des numéros de fichier par algorithme, assurez-vous que les nombres sont valides.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3. <span data-ttu-id="ce4fd-112">Vérifiez les noms de fichier pour vous assurer qu’elles sont conformes aux conventions du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="ce4fd-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4fd-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce4fd-113">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
- [<span data-ttu-id="ce4fd-114">Conventions d’affectation de noms de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce4fd-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
