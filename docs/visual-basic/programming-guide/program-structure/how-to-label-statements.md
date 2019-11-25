---
title: 'Comment : étiqueter des instructions'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: be116ac8046c43e89e44c2d9127c6131e4dfaa52
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347378"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="711e4-102">Comment : étiqueter des instructions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="711e4-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="711e4-103">Statement blocks are made up of lines of code delimited by colons.</span><span class="sxs-lookup"><span data-stu-id="711e4-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="711e4-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span><span class="sxs-lookup"><span data-stu-id="711e4-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="711e4-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="711e4-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="711e4-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span><span class="sxs-lookup"><span data-stu-id="711e4-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="711e4-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span><span class="sxs-lookup"><span data-stu-id="711e4-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="711e4-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span><span class="sxs-lookup"><span data-stu-id="711e4-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="711e4-109">If it does not, the compiler assumes it is a label.</span><span class="sxs-lookup"><span data-stu-id="711e4-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="711e4-110">Labels have their own declaration space and do not interfere with other identifiers.</span><span class="sxs-lookup"><span data-stu-id="711e4-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="711e4-111">A label's scope is the body of the method.</span><span class="sxs-lookup"><span data-stu-id="711e4-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="711e4-112">Label declaration takes precedence in any ambiguous situation.</span><span class="sxs-lookup"><span data-stu-id="711e4-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="711e4-113">Labels can be used only on executable statements inside methods.</span><span class="sxs-lookup"><span data-stu-id="711e4-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="711e4-114">To label a line of code</span><span class="sxs-lookup"><span data-stu-id="711e4-114">To label a line of code</span></span>

<span data-ttu-id="711e4-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span><span class="sxs-lookup"><span data-stu-id="711e4-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="711e4-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span><span class="sxs-lookup"><span data-stu-id="711e4-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="711e4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="711e4-117">See also</span></span>

- [<span data-ttu-id="711e4-118">Instructions</span><span class="sxs-lookup"><span data-stu-id="711e4-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="711e4-119">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="711e4-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="711e4-120">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="711e4-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
