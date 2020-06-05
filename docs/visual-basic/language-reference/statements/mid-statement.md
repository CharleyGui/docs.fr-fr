---
title: Mid, instruction
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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404449"
---
# <a name="mid-statement"></a><span data-ttu-id="e4ad7-102">Mid, instruction</span><span class="sxs-lookup"><span data-stu-id="e4ad7-102">Mid Statement</span></span>
<span data-ttu-id="e4ad7-103">Remplace un nombre spécifié de caractères dans une `String` variable par des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-103">Replaces a specified number of characters in a `String` variable with characters from another string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4ad7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4ad7-104">Syntax</span></span>  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a><span data-ttu-id="e4ad7-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="e4ad7-105">Parts</span></span>  
 `Target`  
 <span data-ttu-id="e4ad7-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-106">Required.</span></span> <span data-ttu-id="e4ad7-107">Nom de la `String` variable à modifier.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-107">Name of the `String` variable to modify.</span></span>  
  
 `Start`  
 <span data-ttu-id="e4ad7-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-108">Required.</span></span> <span data-ttu-id="e4ad7-109">Expression `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-109">`Integer` expression.</span></span> <span data-ttu-id="e4ad7-110">Position du caractère dans `Target` où commence le remplacement de texte.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-110">Character position in `Target` where the replacement of text begins.</span></span> <span data-ttu-id="e4ad7-111">`Start`utilise un index de base un.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-111">`Start` uses a one-based index.</span></span>  
  
 `Length`  
 <span data-ttu-id="e4ad7-112">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-112">Optional.</span></span> <span data-ttu-id="e4ad7-113">Expression `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-113">`Integer` expression.</span></span> <span data-ttu-id="e4ad7-114">Nombre de caractères à remplacer.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-114">Number of characters to replace.</span></span> <span data-ttu-id="e4ad7-115">En cas d’omission, All `String` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-115">If omitted, all of `String` is used.</span></span>  
  
 `StringExpression`  
 <span data-ttu-id="e4ad7-116">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-116">Required.</span></span> <span data-ttu-id="e4ad7-117">`String`expression qui remplace une partie de `Target` .</span><span class="sxs-lookup"><span data-stu-id="e4ad7-117">`String` expression that replaces part of `Target`.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="e4ad7-118">Exceptions</span><span class="sxs-lookup"><span data-stu-id="e4ad7-118">Exceptions</span></span>  
  
|<span data-ttu-id="e4ad7-119">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="e4ad7-119">Exception type</span></span>|<span data-ttu-id="e4ad7-120">Condition</span><span class="sxs-lookup"><span data-stu-id="e4ad7-120">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="e4ad7-121">`Start`<= 0 ou `Length` < 0.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-121">`Start` <= 0 or `Length` < 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4ad7-122">Notes</span><span class="sxs-lookup"><span data-stu-id="e4ad7-122">Remarks</span></span>  
 <span data-ttu-id="e4ad7-123">Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target` .</span><span class="sxs-lookup"><span data-stu-id="e4ad7-123">The number of characters replaced is always less than or equal to the number of characters in `Target`.</span></span>  
  
 <span data-ttu-id="e4ad7-124">Visual Basic a une <xref:Microsoft.VisualBasic.Strings.Mid%2A> fonction et une `Mid` instruction.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-124">Visual Basic has a <xref:Microsoft.VisualBasic.Strings.Mid%2A> function and a `Mid` statement.</span></span> <span data-ttu-id="e4ad7-125">Ces éléments agissent tous deux sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères lorsque l' `Mid` instruction remplace les caractères.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-125">These elements both operate on a specified number of characters in a string, but the `Mid` function returns the characters while the `Mid` statement replaces the characters.</span></span> <span data-ttu-id="e4ad7-126">Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-126">For more information, see <xref:Microsoft.VisualBasic.Strings.Mid%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4ad7-127">L' `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets plutôt que des caractères.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-127">The `MidB` statement of earlier versions of Visual Basic replaces a substring in bytes, rather than characters.</span></span> <span data-ttu-id="e4ad7-128">Il est principalement utilisé pour convertir des chaînes dans des applications DBCS (Double-Byte Character Set).</span><span class="sxs-lookup"><span data-stu-id="e4ad7-128">It is used primarily for converting strings in double-byte character set (DBCS) applications.</span></span> <span data-ttu-id="e4ad7-129">Toutes les chaînes Visual Basic sont au format Unicode et ne `MidB` sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-129">All Visual Basic strings are in Unicode, and `MidB` is no longer supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4ad7-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="e4ad7-130">Example</span></span>  
 <span data-ttu-id="e4ad7-131">Cet exemple utilise l' `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable String par des caractères d’une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="e4ad7-131">This example uses the `Mid` statement to replace a specified number of characters in a string variable with characters from another string.</span></span>  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a><span data-ttu-id="e4ad7-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4ad7-132">Requirements</span></span>  
 <span data-ttu-id="e4ad7-133">**Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="e4ad7-133">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="e4ad7-134">**Module :**`Strings`</span><span class="sxs-lookup"><span data-stu-id="e4ad7-134">**Module:** `Strings`</span></span>  
  
 <span data-ttu-id="e4ad7-135">**Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="e4ad7-135">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4ad7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4ad7-136">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [<span data-ttu-id="e4ad7-137">Chaînes</span><span class="sxs-lookup"><span data-stu-id="e4ad7-137">Strings</span></span>](../../programming-guide/language-features/strings/index.md)
- [<span data-ttu-id="e4ad7-138">Introduction aux chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e4ad7-138">Introduction to Strings in Visual Basic</span></span>](../../programming-guide/language-features/strings/introduction-to-strings.md)
