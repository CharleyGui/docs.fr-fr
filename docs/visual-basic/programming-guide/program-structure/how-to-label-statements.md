---
title: 'Procédure : Étiqueter des instructions'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: 8f04d592c51b6a0630bfe623fd3574555aef9ff8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403211"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="dcd5c-102">Comment : étiqueter des instructions (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dcd5c-102">How to: Label Statements (Visual Basic)</span></span>

<span data-ttu-id="dcd5c-103">Les blocs d’instructions sont constitués de lignes de code séparées par des signes deux-points.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="dcd5c-104">Les lignes de code précédées d’une chaîne ou d’un entier d’identification sont dites *étiquetées*.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="dcd5c-105">Les étiquettes d’instructions sont utilisées pour marquer une ligne de code afin de l’identifier pour une utilisation avec des instructions telles que `On Error Goto` .</span><span class="sxs-lookup"><span data-stu-id="dcd5c-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>

<span data-ttu-id="dcd5c-106">Les étiquettes peuvent être des identificateurs de Visual Basic valides, tels que ceux qui identifient des éléments de programmation, ou des littéraux entiers.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="dcd5c-107">Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie d’un signe deux-points, qu’elle soit suivie ou non d’une instruction sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>

<span data-ttu-id="dcd5c-108">Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à un identificateur déjà défini.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="dcd5c-109">Si ce n’est pas le cas, le compilateur suppose qu’il s’agit d’une étiquette.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-109">If it does not, the compiler assumes it is a label.</span></span>

<span data-ttu-id="dcd5c-110">Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="dcd5c-111">La portée d’une étiquette est le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="dcd5c-112">La déclaration d’étiquette est prioritaire dans toute situation ambiguë.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-112">Label declaration takes precedence in any ambiguous situation.</span></span>

> [!NOTE]
> <span data-ttu-id="dcd5c-113">Les étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-113">Labels can be used only on executable statements inside methods.</span></span>

## <a name="to-label-a-line-of-code"></a><span data-ttu-id="dcd5c-114">Pour étiqueter une ligne de code</span><span class="sxs-lookup"><span data-stu-id="dcd5c-114">To label a line of code</span></span>

<span data-ttu-id="dcd5c-115">Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.</span><span class="sxs-lookup"><span data-stu-id="dcd5c-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>

<span data-ttu-id="dcd5c-116">Par exemple, les lignes de code suivantes sont étiquetées avec `Jump` et `120` , respectivement :</span><span class="sxs-lookup"><span data-stu-id="dcd5c-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>

[!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]

## <a name="see-also"></a><span data-ttu-id="dcd5c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcd5c-117">See also</span></span>

- [<span data-ttu-id="dcd5c-118">Instructions</span><span class="sxs-lookup"><span data-stu-id="dcd5c-118">Statements</span></span>](../language-features/statements.md)
- [<span data-ttu-id="dcd5c-119">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="dcd5c-119">Declared Element Names</span></span>](../language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="dcd5c-120">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="dcd5c-120">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
