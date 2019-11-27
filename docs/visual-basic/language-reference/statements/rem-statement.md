---
title: REM, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346732"
---
# <a name="rem-statement-visual-basic"></a><span data-ttu-id="44e94-102">REM, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44e94-102">REM Statement (Visual Basic)</span></span>
<span data-ttu-id="44e94-103">Utilisé pour inclure des remarques explicatives dans le code source d’un programme.</span><span class="sxs-lookup"><span data-stu-id="44e94-103">Used to include explanatory remarks in the source code of a program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44e94-104">Syntax</span></span>  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a><span data-ttu-id="44e94-105">Composants</span><span class="sxs-lookup"><span data-stu-id="44e94-105">Parts</span></span>  
 `comment`  
 <span data-ttu-id="44e94-106">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="44e94-106">Optional.</span></span> <span data-ttu-id="44e94-107">Texte de tous les commentaires que vous souhaitez inclure.</span><span class="sxs-lookup"><span data-stu-id="44e94-107">The text of any comment you want to include.</span></span> <span data-ttu-id="44e94-108">Un espace est requis entre le mot clé `REM` et `comment`.</span><span class="sxs-lookup"><span data-stu-id="44e94-108">A space is required between the `REM` keyword and `comment`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44e94-109">Notes</span><span class="sxs-lookup"><span data-stu-id="44e94-109">Remarks</span></span>  
 <span data-ttu-id="44e94-110">Vous pouvez placer une instruction `REM` seule sur une ligne, ou vous pouvez la placer sur une ligne après une autre instruction.</span><span class="sxs-lookup"><span data-stu-id="44e94-110">You can put a `REM` statement alone on a line, or you can put it on a line following another statement.</span></span> <span data-ttu-id="44e94-111">L’instruction `REM` doit être la dernière instruction de la ligne.</span><span class="sxs-lookup"><span data-stu-id="44e94-111">The `REM` statement must be the last statement on the line.</span></span> <span data-ttu-id="44e94-112">S’il suit une autre instruction, le `REM` doit être séparé de cette instruction par un espace.</span><span class="sxs-lookup"><span data-stu-id="44e94-112">If it follows another statement, the `REM` must be separated from that statement by a space.</span></span>  
  
 <span data-ttu-id="44e94-113">Vous pouvez utiliser un guillemet simple (`'`) au lieu de `REM`.</span><span class="sxs-lookup"><span data-stu-id="44e94-113">You can use a single quotation mark (`'`) instead of `REM`.</span></span> <span data-ttu-id="44e94-114">Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou s’il se trouve seul sur une ligne.</span><span class="sxs-lookup"><span data-stu-id="44e94-114">This is true whether your comment follows another statement on the same line or sits alone on a line.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="44e94-115">Vous ne pouvez pas continuer une instruction `REM` à l’aide d’une séquence de continuation de ligne (`_`).</span><span class="sxs-lookup"><span data-stu-id="44e94-115">You cannot continue a `REM` statement by using a line-continuation sequence (`_`).</span></span> <span data-ttu-id="44e94-116">Une fois qu’un commentaire commence, le compilateur n’examine pas les caractères pour une signification particulière.</span><span class="sxs-lookup"><span data-stu-id="44e94-116">Once a comment begins, the compiler does not examine the characters for special meaning.</span></span> <span data-ttu-id="44e94-117">Pour un commentaire sur plusieurs lignes, utilisez une autre instruction `REM` ou un symbole de commentaire (`'`) sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="44e94-117">For a multiple-line comment, use another `REM` statement or a comment symbol (`'`) on each line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44e94-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="44e94-118">Example</span></span>  
 <span data-ttu-id="44e94-119">L’exemple suivant illustre l’instruction `REM`, qui est utilisée pour inclure des remarques explicatives dans un programme.</span><span class="sxs-lookup"><span data-stu-id="44e94-119">The following example illustrates the `REM` statement, which is used to include explanatory remarks in a program.</span></span> <span data-ttu-id="44e94-120">Il montre également l’alternative à l’utilisation du caractère guillemet simple (`'`) au lieu de `REM`.</span><span class="sxs-lookup"><span data-stu-id="44e94-120">It also shows the alternative of using the single quotation-mark character (`'`) instead of `REM`.</span></span>  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="44e94-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44e94-121">See also</span></span>

- [<span data-ttu-id="44e94-122">Commentaires dans le code</span><span class="sxs-lookup"><span data-stu-id="44e94-122">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [<span data-ttu-id="44e94-123">Guide pratique : diviser et combiner des instructions dans le code</span><span class="sxs-lookup"><span data-stu-id="44e94-123">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
