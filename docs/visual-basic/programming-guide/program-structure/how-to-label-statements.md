---
title: 'Procédure : Instructions de l’étiquette (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
ms.openlocfilehash: cbb80d94dc8280aa67859c89daad1520ce4e9669
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648748"
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="4c286-102">Procédure : Instructions de l’étiquette (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c286-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="4c286-103">Blocs d’instructions sont constituées de lignes de code délimités par le signe deux-points.</span><span class="sxs-lookup"><span data-stu-id="4c286-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="4c286-104">Lignes de code, précédé d’une chaîne ou entier identifiant sont dites *intitulée*.</span><span class="sxs-lookup"><span data-stu-id="4c286-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="4c286-105">Les étiquettes d’instruction sont utilisées pour marquer une ligne de code pour identifier pour une utilisation avec des instructions telles que `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="4c286-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="4c286-106">Les étiquettes peuvent être soit des identificateurs Visual Basic valides, telles que celles qui identifient les éléments de programmation, ou les littéraux d’entier.</span><span class="sxs-lookup"><span data-stu-id="4c286-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="4c286-107">Une étiquette doit apparaître au début d’une ligne de code source et doit être suivie par un signe deux-points, indépendamment de si elle est suivie par une instruction sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="4c286-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="4c286-108">Le compilateur identifie les étiquettes en vérifiant si le début de la ligne correspond à n’importe quel identificateur déjà défini.</span><span class="sxs-lookup"><span data-stu-id="4c286-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="4c286-109">Si elle n’est pas le cas, le compilateur suppose que c’est une étiquette.</span><span class="sxs-lookup"><span data-stu-id="4c286-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="4c286-110">Les étiquettes ont leur propre espace de déclaration et n’interfèrent pas avec d’autres identificateurs.</span><span class="sxs-lookup"><span data-stu-id="4c286-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="4c286-111">Portée d’une étiquette est le corps de la méthode.</span><span class="sxs-lookup"><span data-stu-id="4c286-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="4c286-112">Déclaration d’étiquette est prioritaire dans une situation ambiguë.</span><span class="sxs-lookup"><span data-stu-id="4c286-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c286-113">Étiquettes peuvent être utilisées uniquement sur des instructions exécutables à l’intérieur de méthodes.</span><span class="sxs-lookup"><span data-stu-id="4c286-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="4c286-114">Pour étiqueter une ligne de code</span><span class="sxs-lookup"><span data-stu-id="4c286-114">To label a line of code</span></span>  
  
- <span data-ttu-id="4c286-115">Placez un identificateur, suivi d’un signe deux-points, au début de la ligne de code source.</span><span class="sxs-lookup"><span data-stu-id="4c286-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="4c286-116">Par exemple, les lignes de code suivantes sont étiquetés avec `Jump` et `120`, respectivement :</span><span class="sxs-lookup"><span data-stu-id="4c286-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#708)]  
  
## <a name="see-also"></a><span data-ttu-id="4c286-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c286-117">See also</span></span>

- [<span data-ttu-id="4c286-118">Instructions</span><span class="sxs-lookup"><span data-stu-id="4c286-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="4c286-119">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="4c286-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="4c286-120">Structure de programme et conventions de codage</span><span class="sxs-lookup"><span data-stu-id="4c286-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
