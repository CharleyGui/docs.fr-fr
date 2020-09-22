---
title: Fin d'instruction attendue
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 9141400afc651629df381e0a655e2d7b9da2e45d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874417"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="2046a-102">Fin d'instruction attendue</span><span class="sxs-lookup"><span data-stu-id="2046a-102">End of statement expected</span></span>

<span data-ttu-id="2046a-103">L’instruction est syntaxiquement terminée, mais un élément de programmation supplémentaire suit l’élément qui termine l’instruction.</span><span class="sxs-lookup"><span data-stu-id="2046a-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="2046a-104">Une marque de fin de ligne est requise à la fin de chaque instruction.</span><span class="sxs-lookup"><span data-stu-id="2046a-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="2046a-105">Une marque de fin de ligne divise les caractères d’un fichier source Visual Basic en lignes.</span><span class="sxs-lookup"><span data-stu-id="2046a-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="2046a-106">Les marques de fin de ligne sont, par exemple, le caractère de retour chariot Unicode (&HD), le caractère de saut de ligne Unicode (&HA) et le caractère de retour chariot Unicode suivi du caractère de saut de ligne Unicode.</span><span class="sxs-lookup"><span data-stu-id="2046a-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="2046a-107">Pour plus d’informations sur les terminateurs de ligne, consultez la [spécification du langage Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="2046a-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="2046a-108">**ID d’erreur :** BC30205</span><span class="sxs-lookup"><span data-stu-id="2046a-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2046a-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2046a-109">To correct this error</span></span>
  
1. <span data-ttu-id="2046a-110">Vérifiez si deux instructions différentes ont été placées par inadvertance sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="2046a-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2. <span data-ttu-id="2046a-111">Insérez un terminateur de ligne après l’élément qui termine l’instruction.</span><span class="sxs-lookup"><span data-stu-id="2046a-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2046a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2046a-112">See also</span></span>

- [<span data-ttu-id="2046a-113">Procédure : Diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="2046a-113">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="2046a-114">Publication</span><span class="sxs-lookup"><span data-stu-id="2046a-114">Statements</span></span>](../../programming-guide/language-features/statements.md)
