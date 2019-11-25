---
title: 'Comment : diviser et combiner des instructions dans le code'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: f1a24c001cd20acc7663fb4cbe60e7e35a9c8fc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347435"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="d7403-102">Procédure : diviser et combiner des instructions dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7403-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="d7403-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span><span class="sxs-lookup"><span data-stu-id="d7403-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="d7403-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span><span class="sxs-lookup"><span data-stu-id="d7403-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="d7403-105">In such cases, you should consider breaking the single long statement into several lines.</span><span class="sxs-lookup"><span data-stu-id="d7403-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="d7403-106">To break a single statement into multiple lines</span><span class="sxs-lookup"><span data-stu-id="d7403-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="d7403-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span><span class="sxs-lookup"><span data-stu-id="d7403-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="d7403-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span><span class="sxs-lookup"><span data-stu-id="d7403-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d7403-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span><span class="sxs-lookup"><span data-stu-id="d7403-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="d7403-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="d7403-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="d7403-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span><span class="sxs-lookup"><span data-stu-id="d7403-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="d7403-112">Using this sequence makes your code easier to read, both online and when printed.</span><span class="sxs-lookup"><span data-stu-id="d7403-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="d7403-113">The line-continuation character must be the last character on a line.</span><span class="sxs-lookup"><span data-stu-id="d7403-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="d7403-114">You can't follow it with anything else on the same line.</span><span class="sxs-lookup"><span data-stu-id="d7403-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="d7403-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span><span class="sxs-lookup"><span data-stu-id="d7403-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="d7403-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span><span class="sxs-lookup"><span data-stu-id="d7403-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="d7403-117">You can't continue a comment by using a line-continuation character.</span><span class="sxs-lookup"><span data-stu-id="d7403-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="d7403-118">The compiler doesn't examine the characters in a comment for special meaning.</span><span class="sxs-lookup"><span data-stu-id="d7403-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="d7403-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span><span class="sxs-lookup"><span data-stu-id="d7403-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="d7403-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span><span class="sxs-lookup"><span data-stu-id="d7403-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="d7403-121">To place multiple statements on the same line</span><span class="sxs-lookup"><span data-stu-id="d7403-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="d7403-122">Separate the statements with a colon (`:`), as in the following example:</span><span class="sxs-lookup"><span data-stu-id="d7403-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="d7403-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7403-123">See also</span></span>

- [<span data-ttu-id="d7403-124">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="d7403-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="d7403-125">Instructions</span><span class="sxs-lookup"><span data-stu-id="d7403-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
