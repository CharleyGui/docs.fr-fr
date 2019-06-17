---
title: Mid, instruction (Visual Basic)
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
ms.openlocfilehash: ff3b908e2805f4d51463a82d90f2305efc9f1608
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041584"
---
# <a name="mid-statement"></a><span data-ttu-id="87cdf-102">Mid, instruction</span><span class="sxs-lookup"><span data-stu-id="87cdf-102">Mid Statement</span></span>
<span data-ttu-id="87cdf-103">Remplace un nombre spécifié de caractères dans un `String` variable avec des caractères à partir d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="87cdf-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87cdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87cdf-104">Syntax</span></span>  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="87cdf-105">Composants</span><span class="sxs-lookup"><span data-stu-id="87cdf-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="87cdf-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="87cdf-106">Required.</span></span> <span data-ttu-id="87cdf-107">Nom de la `String` variable à modifier.</span><span class="sxs-lookup"><span data-stu-id="87cdf-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="87cdf-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="87cdf-108">Required.</span></span> <span data-ttu-id="87cdf-109">`Integer` expression.</span><span class="sxs-lookup"><span data-stu-id="87cdf-109">`Integer` expression.</span></span> <span data-ttu-id="87cdf-110">Position du caractère dans `Target` où commence le remplacement de texte.</span><span class="sxs-lookup"><span data-stu-id="87cdf-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="87cdf-111">`Start` utilise un index de base un.</span><span class="sxs-lookup"><span data-stu-id="87cdf-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="87cdf-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="87cdf-112">Optional.</span></span> <span data-ttu-id="87cdf-113">`Integer` expression.</span><span class="sxs-lookup"><span data-stu-id="87cdf-113">`Integer` expression.</span></span> <span data-ttu-id="87cdf-114">Nombre de caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="87cdf-114">Number of characters to replace.</span></span> <span data-ttu-id="87cdf-115">Si omis, tous les `String` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="87cdf-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="87cdf-116">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="87cdf-116">Required.</span></span> <span data-ttu-id="87cdf-117">`String` Expression qui remplace une partie de `Target`.</span><span class="sxs-lookup"><span data-stu-id="87cdf-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="87cdf-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="87cdf-118">Exceptions</span></span>  
  
|<span data-ttu-id="87cdf-119">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="87cdf-119">Exception type</span></span>|<span data-ttu-id="87cdf-120">Condition</span><span class="sxs-lookup"><span data-stu-id="87cdf-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="87cdf-121">`Start` < = 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="87cdf-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87cdf-122">Notes</span><span class="sxs-lookup"><span data-stu-id="87cdf-122">Remarks</span></span>  
 <span data-ttu-id="87cdf-123">Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.</span><span class="sxs-lookup"><span data-stu-id="87cdf-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="87cdf-124">Visual Basic a un <xref:Microsoft.VisualBasic.Strings.Mid%2A> (fonction) et un `Mid` instruction.</span><span class="sxs-lookup"><span data-stu-id="87cdf-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="87cdf-125">Ces éléments fonctionnent à la fois sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères lors de la `Mid` instruction remplace les caractères.</span><span class="sxs-lookup"><span data-stu-id="87cdf-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="87cdf-126">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="87cdf-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87cdf-127">La `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets, plutôt que des caractères.</span><span class="sxs-lookup"><span data-stu-id="87cdf-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="87cdf-128">Il est utilisé principalement pour la conversion de chaînes dans les applications de jeu codés sur deux octets.</span><span class="sxs-lookup"><span data-stu-id="87cdf-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="87cdf-129">Toutes les chaînes Visual Basic sont au format Unicode, et `MidB` n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="87cdf-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87cdf-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="87cdf-130">Example</span></span>  
 <span data-ttu-id="87cdf-131">Cet exemple utilise la `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable de chaîne avec des caractères à partir d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="87cdf-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="87cdf-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="87cdf-132">Requirements</span></span>  
 <span data-ttu-id="87cdf-133">**Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="87cdf-133">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="87cdf-134">**Module :** `Strings`</span><span class="sxs-lookup"><span data-stu-id="87cdf-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="87cdf-135">**Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="87cdf-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87cdf-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87cdf-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="87cdf-137">Chaînes</span><span class="sxs-lookup"><span data-stu-id="87cdf-137">Strings</span></span>](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="87cdf-138">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87cdf-138">Introduction to Strings in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
