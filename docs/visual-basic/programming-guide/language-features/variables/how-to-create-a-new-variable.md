---
title: 'Comment : créer une variable'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: 501c8f3aff4c5b204d231bdc26213e13d125a7cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410527"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="889e6-102">Comment : créer une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="889e6-102">How to: Create a New Variable (Visual Basic)</span></span>

<span data-ttu-id="889e6-103">Vous créez une variable avec une [instruction Dim](../../../language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="889e6-103">You create a variable with a [Dim Statement](../../../language-reference/statements/dim-statement.md).</span></span>

### <a name="to-create-a-new-variable"></a><span data-ttu-id="889e6-104">Pour créer une variable</span><span class="sxs-lookup"><span data-stu-id="889e6-104">To create a new variable</span></span>

1. <span data-ttu-id="889e6-105">Déclarez la variable dans une `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="889e6-105">Declare the variable in a `Dim` statement.</span></span>

    ```vb
    Dim newCustomer
    ```

2. <span data-ttu-id="889e6-106">Inclure des spécifications pour les caractéristiques de la variable, telles que [Private](../../../language-reference/modifiers/private.md), [static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md)ou [WithEvents](../../../language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="889e6-106">Include specifications for the variable's characteristics, such as [Private](../../../language-reference/modifiers/private.md), [Static](../../../language-reference/modifiers/static.md), [Shadows](../../../language-reference/modifiers/shadows.md), or [WithEvents](../../../language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="889e6-107">Pour plus d’informations, consultez [caractéristiques des éléments déclarés](../declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="889e6-107">For more information, see [Declared Element Characteristics](../declared-elements/declared-element-characteristics.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

    <span data-ttu-id="889e6-108">Vous n’avez pas besoin du `Dim` mot clé si vous utilisez d’autres mots clés dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="889e6-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>

3. <span data-ttu-id="889e6-109">Suivez les spécifications avec le nom de la variable, qui doit suivre Visual Basic règles et conventions.</span><span class="sxs-lookup"><span data-stu-id="889e6-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="889e6-110">Pour plus d’informations, consultez [noms d’éléments déclarés](../declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="889e6-110">For more information, see [Declared Element Names](../declared-elements/declared-element-names.md).</span></span>

    ```vb
    Public Static newCustomer
    ```

4. <span data-ttu-id="889e6-111">Suivez le nom avec la clause [As](../../../language-reference/statements/as-clause.md) pour spécifier le type de données de la variable.</span><span class="sxs-lookup"><span data-stu-id="889e6-111">Follow the name with the [As](../../../language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>

    ```vb
    Public Static newCustomer As Customer
    ```

    <span data-ttu-id="889e6-112">Si vous ne spécifiez pas le type de données, il utilise la valeur par défaut : `Object` .</span><span class="sxs-lookup"><span data-stu-id="889e6-112">If you do not specify the data type, it uses the default: `Object`.</span></span>

5. <span data-ttu-id="889e6-113">Suivez la `As` clause avec un signe égal ( `=` ) et suivez le signe égal avec la valeur initiale de la variable.</span><span class="sxs-lookup"><span data-stu-id="889e6-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>

    <span data-ttu-id="889e6-114">Visual Basic affecte la valeur spécifiée à la variable chaque fois qu’il exécute l' `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="889e6-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="889e6-115">Si vous ne spécifiez pas de valeur initiale, Visual Basic affecte la valeur initiale par défaut pour le type de données de la variable lorsqu’il entre pour la première fois dans le code qui contient l' `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="889e6-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>

    <span data-ttu-id="889e6-116">Si la variable est un type référence, vous pouvez créer une instance de sa classe en incluant le mot clé [New Operator](../../../language-reference/operators/new-operator.md) dans la `As` clause.</span><span class="sxs-lookup"><span data-stu-id="889e6-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="889e6-117">Si vous n’utilisez pas `New` , la valeur initiale de la variable est [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="889e6-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../language-reference/nothing.md).</span></span>

    ```vb
    Public Static newCustomer As New Customer
    ```

## <a name="see-also"></a><span data-ttu-id="889e6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="889e6-118">See also</span></span>

- [<span data-ttu-id="889e6-119">Variables</span><span class="sxs-lookup"><span data-stu-id="889e6-119">Variables</span></span>](index.md)
- [<span data-ttu-id="889e6-120">Déclaration de variable</span><span class="sxs-lookup"><span data-stu-id="889e6-120">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="889e6-121">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="889e6-121">Declared Element Names</span></span>](../declared-elements/declared-element-names.md)
- [<span data-ttu-id="889e6-122">Caractéristiques des éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="889e6-122">Declared Element Characteristics</span></span>](../declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="889e6-123">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="889e6-123">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="889e6-124">Instructions</span><span class="sxs-lookup"><span data-stu-id="889e6-124">Statements</span></span>](../../../language-reference/statements/index.md)
- [<span data-ttu-id="889e6-125">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="889e6-125">Local Type Inference</span></span>](local-type-inference.md)
- [<span data-ttu-id="889e6-126">Instruction Option Infer</span><span class="sxs-lookup"><span data-stu-id="889e6-126">Option Infer Statement</span></span>](../../../language-reference/statements/option-infer-statement.md)
