---
title: New, opérateur
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 27b5b4516ef729045036c36fedc24b6c576a4f61
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348315"
---
# <a name="new-operator-visual-basic"></a><span data-ttu-id="56a93-102">New, opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56a93-102">New Operator (Visual Basic)</span></span>

<span data-ttu-id="56a93-103">Introduit une clause `New` pour créer une nouvelle instance d’objet, spécifie une contrainte de constructeur sur un paramètre de type, ou identifie une procédure `Sub` comme un constructeur de classe.</span><span class="sxs-lookup"><span data-stu-id="56a93-103">Introduces a `New` clause to create a new object instance, specifies a constructor constraint on a type parameter, or identifies a `Sub` procedure as a class constructor.</span></span>

## <a name="remarks"></a><span data-ttu-id="56a93-104">Notes</span><span class="sxs-lookup"><span data-stu-id="56a93-104">Remarks</span></span>

<span data-ttu-id="56a93-105">Dans une déclaration ou une instruction d’assignation, une clause `New` doit spécifier une classe définie à partir de laquelle l’instance peut être créée.</span><span class="sxs-lookup"><span data-stu-id="56a93-105">In a declaration or assignment statement, a `New` clause must specify a defined class from which the instance can be created.</span></span> <span data-ttu-id="56a93-106">Cela signifie que la classe doit exposer un ou plusieurs constructeurs auxquels le code appelant peut accéder.</span><span class="sxs-lookup"><span data-stu-id="56a93-106">This means that the class must expose one or more constructors that the calling code can access.</span></span>

<span data-ttu-id="56a93-107">Vous pouvez utiliser une clause `New` dans une instruction de déclaration ou une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="56a93-107">You can use a `New` clause in a declaration statement or an assignment statement.</span></span> <span data-ttu-id="56a93-108">Lorsque l’instruction s’exécute, elle appelle le constructeur approprié de la classe spécifiée, en passant tous les arguments que vous avez fournis.</span><span class="sxs-lookup"><span data-stu-id="56a93-108">When the statement runs, it calls the appropriate constructor of the specified class, passing any arguments you have supplied.</span></span> <span data-ttu-id="56a93-109">L’exemple suivant illustre cela en créant des instances d’une classe `Customer` qui a deux constructeurs, un qui n’accepte aucun paramètre et un qui accepte un paramètre de chaîne :</span><span class="sxs-lookup"><span data-stu-id="56a93-109">The following example demonstrates this by creating instances of a `Customer` class that has two constructors, one that takes no parameters and one that takes a string parameter:</span></span>

[!code-vb[VbVbalrKeywords#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#11)]

<span data-ttu-id="56a93-110">Étant donné que les tableaux sont des classes, `New` pouvez créer une nouvelle instance de tableau, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="56a93-110">Since arrays are classes, `New` can create a new array instance, as shown in the following example:</span></span>

[!code-vb[VbVbalrKeywords#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class6.vb#12)]

<span data-ttu-id="56a93-111">Le common language runtime (CLR) lève une erreur de <xref:System.OutOfMemoryException> si la mémoire est insuffisante pour créer la nouvelle instance.</span><span class="sxs-lookup"><span data-stu-id="56a93-111">The common language runtime (CLR) throws an <xref:System.OutOfMemoryException> error if there is insufficient memory to create the new instance.</span></span>

> [!NOTE]
> <span data-ttu-id="56a93-112">Le mot clé `New` est également utilisé dans les listes de paramètres de type pour spécifier que le type fourni doit exposer un constructeur sans paramètre accessible.</span><span class="sxs-lookup"><span data-stu-id="56a93-112">The `New` keyword is also used in type parameter lists to specify that the supplied type must expose an accessible parameterless constructor.</span></span> <span data-ttu-id="56a93-113">Pour plus d’informations sur les paramètres de type et les contraintes, consultez [type list](../statements/type-list.md).</span><span class="sxs-lookup"><span data-stu-id="56a93-113">For more information about type parameters and constraints, see [Type List](../statements/type-list.md).</span></span>

<span data-ttu-id="56a93-114">Pour créer une procédure constructeur pour une classe, définissez le nom d’une `Sub` procédure sur le mot clé `New`.</span><span class="sxs-lookup"><span data-stu-id="56a93-114">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="56a93-115">Pour plus d’informations, consultez durée de vie d’un [objet : comment les objets sont créés et détruits](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="56a93-115">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

<span data-ttu-id="56a93-116">Le mot clé `New` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="56a93-116">The `New` keyword can be used in these contexts:</span></span>

- [<span data-ttu-id="56a93-117">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="56a93-117">Dim Statement</span></span>](../statements/dim-statement.md)
- [<span data-ttu-id="56a93-118">Of</span><span class="sxs-lookup"><span data-stu-id="56a93-118">Of</span></span>](../statements/of-clause.md)
- [<span data-ttu-id="56a93-119">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="56a93-119">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="56a93-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56a93-120">See also</span></span>

- <xref:System.OutOfMemoryException>
- [<span data-ttu-id="56a93-121">Mots clés</span><span class="sxs-lookup"><span data-stu-id="56a93-121">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="56a93-122">Liste de types</span><span class="sxs-lookup"><span data-stu-id="56a93-122">Type List</span></span>](../statements/type-list.md)
- [<span data-ttu-id="56a93-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56a93-123">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="56a93-124">Durée de vie d’un objet : création et destruction des objets</span><span class="sxs-lookup"><span data-stu-id="56a93-124">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
