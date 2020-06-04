---
title: 'Procédure : Diviser et combiner des instructions dans le code'
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
ms.openlocfilehash: c78cbeaa5c2df2d4f2e3cce2b5b3fb8048ff3388
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403250"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="bb4da-102">Procédure : diviser et combiner des instructions dans le code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb4da-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="bb4da-103">Lors de l’écriture de votre code, vous pouvez parfois créer des instructions longues qui nécessitent un défilement horizontal dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="bb4da-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="bb4da-104">Bien que cela n’affecte pas la manière dont votre code s’exécute, cela complique la lecture du code tel qu’il apparaît sur le moniteur.</span><span class="sxs-lookup"><span data-stu-id="bb4da-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="bb4da-105">Dans ce cas, vous devez envisager de fractionner une seule instruction longue en plusieurs lignes.</span><span class="sxs-lookup"><span data-stu-id="bb4da-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="bb4da-106">Pour scinder une seule instruction en plusieurs lignes</span><span class="sxs-lookup"><span data-stu-id="bb4da-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="bb4da-107">Utilisez le caractère de continuation de ligne, qui est un trait de soulignement ( `_` ), à l’endroit où vous souhaitez que la ligne s’arrête.</span><span class="sxs-lookup"><span data-stu-id="bb4da-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="bb4da-108">Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne (retour chariot) ou (à partir de la version 16,0) d’un commentaire suivi d’un retour chariot.</span><span class="sxs-lookup"><span data-stu-id="bb4da-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bb4da-109">Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic continue implicitement l’instruction sur la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="bb4da-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="bb4da-110">Pour obtenir la liste des éléments syntaxiques pour lesquels vous pouvez omettre le caractère de continuation de ligne, consultez « continuation de ligne implicite » dans les [instructions](../language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="bb4da-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../language-features/statements.md).</span></span>

  <span data-ttu-id="bb4da-111">Dans l’exemple suivant, l’instruction est divisée en quatre lignes avec des caractères de continuation de ligne qui terminent tous sauf la dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="bb4da-112">L’utilisation de cette séquence rend votre code plus facile à lire, en ligne et à l’impression.</span><span class="sxs-lookup"><span data-stu-id="bb4da-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="bb4da-113">Le caractère de continuation de ligne doit être le dernier caractère d’une ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="bb4da-114">Vous ne pouvez pas le suivre avec d’autres éléments sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="bb4da-115">Il existe certaines limitations quant à l’emplacement où vous pouvez utiliser le caractère de continuation de ligne. par exemple, vous ne pouvez pas l’utiliser au milieu d’un nom d’argument.</span><span class="sxs-lookup"><span data-stu-id="bb4da-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="bb4da-116">Vous pouvez arrêter une liste d’arguments avec le caractère de continuation de ligne, mais les noms individuels des arguments doivent rester intacts.</span><span class="sxs-lookup"><span data-stu-id="bb4da-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="bb4da-117">Vous ne pouvez pas continuer un commentaire en utilisant un caractère de continuation de ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="bb4da-118">Le compilateur n’examine pas les caractères d’un commentaire pour une signification particulière.</span><span class="sxs-lookup"><span data-stu-id="bb4da-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="bb4da-119">Pour un commentaire de plusieurs lignes, répétez le symbole de commentaire ( `'` ) sur chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="bb4da-120">Bien que la méthode recommandée consiste à placer chaque instruction sur une ligne distincte, Visual Basic vous permet également de placer plusieurs instructions sur la même ligne.</span><span class="sxs-lookup"><span data-stu-id="bb4da-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="bb4da-121">Pour placer plusieurs instructions sur la même ligne</span><span class="sxs-lookup"><span data-stu-id="bb4da-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="bb4da-122">Séparez les instructions par un signe deux-points ( `:` ), comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="bb4da-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="bb4da-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb4da-123">See also</span></span>

- [<span data-ttu-id="bb4da-124">Structure de programme et conventions de code</span><span class="sxs-lookup"><span data-stu-id="bb4da-124">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="bb4da-125">Instructions</span><span class="sxs-lookup"><span data-stu-id="bb4da-125">Statements</span></span>](../language-features/statements.md)
