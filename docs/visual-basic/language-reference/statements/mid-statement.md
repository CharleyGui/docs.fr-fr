---
title: Instruction Mid (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963550"
---
# <a name="mid-statement"></a><span data-ttu-id="55744-102">Mid, instruction</span><span class="sxs-lookup"><span data-stu-id="55744-102">Mid Statement</span></span>
<span data-ttu-id="55744-103">Remplace un nombre spécifié de caractères dans une `String` variable par des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="55744-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55744-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55744-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="55744-105">Composants</span><span class="sxs-lookup"><span data-stu-id="55744-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="55744-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="55744-106">Required.</span></span> <span data-ttu-id="55744-107">Nom de la `String` variable à modifier.</span><span class="sxs-lookup"><span data-stu-id="55744-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="55744-108">Requis.</span><span class="sxs-lookup"><span data-stu-id="55744-108">Required.</span></span> <span data-ttu-id="55744-109">`Integer`formule.</span><span class="sxs-lookup"><span data-stu-id="55744-109">`Integer` expression.</span></span> <span data-ttu-id="55744-110">Position du caractère `Target` dans où commence le remplacement de texte.</span><span class="sxs-lookup"><span data-stu-id="55744-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="55744-111">`Start`utilise un index de base un.</span><span class="sxs-lookup"><span data-stu-id="55744-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="55744-112">facultatif.</span><span class="sxs-lookup"><span data-stu-id="55744-112">Optional.</span></span> <span data-ttu-id="55744-113">`Integer`formule.</span><span class="sxs-lookup"><span data-stu-id="55744-113">`Integer` expression.</span></span> <span data-ttu-id="55744-114">Nombre de caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="55744-114">Number of characters to replace.</span></span> <span data-ttu-id="55744-115">En cas d' `String` omission, All est utilisé.</span><span class="sxs-lookup"><span data-stu-id="55744-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="55744-116">Requis.</span><span class="sxs-lookup"><span data-stu-id="55744-116">Required.</span></span> <span data-ttu-id="55744-117">`String`expression qui remplace une partie `Target`de.</span><span class="sxs-lookup"><span data-stu-id="55744-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="55744-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="55744-118">Exceptions</span></span>  
  
|<span data-ttu-id="55744-119">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="55744-119">Exception type</span></span>|<span data-ttu-id="55744-120">Condition</span><span class="sxs-lookup"><span data-stu-id="55744-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="55744-121">`Start`< = 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="55744-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55744-122">Notes</span><span class="sxs-lookup"><span data-stu-id="55744-122">Remarks</span></span>  
 <span data-ttu-id="55744-123">Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.</span><span class="sxs-lookup"><span data-stu-id="55744-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="55744-124">Visual Basic a une <xref:Microsoft.VisualBasic.Strings.Mid%2A> fonction et une `Mid` instruction.</span><span class="sxs-lookup"><span data-stu-id="55744-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="55744-125">Ces éléments agissent tous deux sur un nombre spécifié de caractères dans une chaîne, mais `Mid` la fonction retourne les caractères lorsque `Mid` l’instruction remplace les caractères.</span><span class="sxs-lookup"><span data-stu-id="55744-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="55744-126">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="55744-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55744-127">L' `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets plutôt que des caractères.</span><span class="sxs-lookup"><span data-stu-id="55744-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="55744-128">Il est principalement utilisé pour convertir des chaînes dans des applications DBCS (Double-Byte Character Set).</span><span class="sxs-lookup"><span data-stu-id="55744-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="55744-129">Toutes les chaînes Visual Basic sont au format Unicode `MidB` et ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="55744-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55744-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="55744-130">Example</span></span>  
 <span data-ttu-id="55744-131">Cet exemple utilise l' `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable String par des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="55744-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="55744-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55744-132">Requirements</span></span>  
 <span data-ttu-id="55744-133">**Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="55744-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="55744-134">**Module:** `Strings`</span><span class="sxs-lookup"><span data-stu-id="55744-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="55744-135">**Chargeur** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="55744-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55744-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55744-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="55744-137">Chaînes</span><span class="sxs-lookup"><span data-stu-id="55744-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="55744-138">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55744-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
