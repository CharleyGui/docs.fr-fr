---
title: Nothing et chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d4c7ee6d13334617a80abb845af52bf388a12797
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072520"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="19839-102">Nothing et les chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19839-102">Nothing and Strings in Visual Basic</span></span>

<span data-ttu-id="19839-103">Le runtime Visual Basic et le .NET Framework évaluer `Nothing` différemment lorsqu’il s’agit de chaînes.</span><span class="sxs-lookup"><span data-stu-id="19839-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="19839-104">Visual Basic Runtime et le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="19839-104">Visual Basic Runtime and the .NET Framework</span></span>  

 <span data-ttu-id="19839-105">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="19839-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="19839-106">Le runtime Visual Basic évalue généralement `Nothing` comme une chaîne vide ("").</span><span class="sxs-lookup"><span data-stu-id="19839-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="19839-107">Toutefois, le .NET Framework ne lève pas d’exception et lève une exception chaque fois qu’une tentative est effectuée pour effectuer une opération de chaîne sur `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="19839-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19839-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19839-108">See also</span></span>

- [<span data-ttu-id="19839-109">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19839-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
