---
title: "Comment : créer une chaîne à partir d'un tableau de valeurs Char"
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344384"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="b9acc-102">Comment : créer une chaîne à partir d'un tableau de valeurs Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9acc-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="b9acc-103">Cet exemple crée la chaîne « ABCD » à partir de caractères individuels.</span><span class="sxs-lookup"><span data-stu-id="b9acc-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9acc-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b9acc-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9acc-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b9acc-105">Compiling the Code</span></span>  
 <span data-ttu-id="b9acc-106">Cette méthode n’a pas d’exigences particulières.</span><span class="sxs-lookup"><span data-stu-id="b9acc-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="b9acc-107">La syntaxe `"a"c`, où un seul `c` suit un caractère unique entre guillemets, est utilisé pour créer un littéral de caractère.</span><span class="sxs-lookup"><span data-stu-id="b9acc-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b9acc-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="b9acc-108">Robust Programming</span></span>  
 <span data-ttu-id="b9acc-109">Les caractères null (équivalents à `Chr(0)`) dans la chaîne entraînent des résultats inattendus lors de l’utilisation de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="b9acc-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="b9acc-110">Le caractère null sera inclus avec la chaîne, mais les caractères qui suivent le caractère NULL ne seront pas affichés dans certaines situations.</span><span class="sxs-lookup"><span data-stu-id="b9acc-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9acc-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9acc-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="b9acc-112">Char (type de données)</span><span class="sxs-lookup"><span data-stu-id="b9acc-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="b9acc-113">Types de données</span><span class="sxs-lookup"><span data-stu-id="b9acc-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
