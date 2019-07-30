---
title: Délégués
description: Découvrez comment utiliser des délégués dans F#.
ms.date: 05/16/2016
ms.openlocfilehash: 65875897d5fc4b2ac66f1dfbe913f29fb74137cd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630373"
---
# <a name="delegates"></a><span data-ttu-id="40791-103">Délégués</span><span class="sxs-lookup"><span data-stu-id="40791-103">Delegates</span></span>

<span data-ttu-id="40791-104">Un délégué représente un appel de fonction en tant qu’objet.</span><span class="sxs-lookup"><span data-stu-id="40791-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="40791-105">Dans F#, vous devez normalement utiliser des valeurs de fonction pour représenter des fonctions comme valeurs de première classe. Toutefois, les délégués sont utilisés dans le .NET Framework et sont donc nécessaires lorsque vous interagissez avec les API qui les attendent.</span><span class="sxs-lookup"><span data-stu-id="40791-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="40791-106">Ils peuvent également être utilisés lors de la création de bibliothèques conçues pour une utilisation à partir d’autres langages de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40791-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="40791-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40791-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="40791-108">Notes</span><span class="sxs-lookup"><span data-stu-id="40791-108">Remarks</span></span>

<span data-ttu-id="40791-109">Dans la syntaxe précédente, `type1` représente le type d’argument ou les `type2` types et représente le type de retour.</span><span class="sxs-lookup"><span data-stu-id="40791-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="40791-110">Les types d’arguments représentés par `type1` sont automatiquement curryfiés.</span><span class="sxs-lookup"><span data-stu-id="40791-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="40791-111">Cela suggère que pour ce type, vous utilisez un formulaire de tuple si les arguments de la fonction cible sont curryfiés, et un tuple entre parenthèses pour les arguments qui se trouvent déjà dans le formulaire de Tuple.</span><span class="sxs-lookup"><span data-stu-id="40791-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="40791-112">La curryfication automatique supprime un jeu de parenthèses, laissant un argument de tuple qui correspond à la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="40791-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="40791-113">Reportez-vous à l’exemple de code pour la syntaxe que vous devez utiliser dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="40791-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="40791-114">Les délégués peuvent être attachés à des valeurs de fonction et à F# des méthodes statiques ou d’instance.</span><span class="sxs-lookup"><span data-stu-id="40791-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="40791-115">F#les valeurs de fonction peuvent être passées directement comme arguments aux constructeurs délégués.</span><span class="sxs-lookup"><span data-stu-id="40791-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="40791-116">Pour une méthode statique, vous construisez le délégué à l’aide du nom de la classe et de la méthode.</span><span class="sxs-lookup"><span data-stu-id="40791-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="40791-117">Pour une méthode d’instance, vous fournissez l’instance d’objet et la méthode dans un seul argument.</span><span class="sxs-lookup"><span data-stu-id="40791-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="40791-118">Dans les deux cas, l’opérateur d’accès`.`aux membres () est utilisé.</span><span class="sxs-lookup"><span data-stu-id="40791-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="40791-119">La `Invoke` méthode sur le type délégué appelle la fonction encapsulée.</span><span class="sxs-lookup"><span data-stu-id="40791-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="40791-120">En outre, les délégués peuvent être passés en tant que valeurs de fonction en référençant le nom de la méthode Invoke sans les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="40791-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="40791-121">Le code suivant illustre la syntaxe de création de délégués qui représentent différentes méthodes dans une classe.</span><span class="sxs-lookup"><span data-stu-id="40791-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="40791-122">Selon que la méthode est une méthode statique ou une méthode d’instance, et si elle a des arguments dans le formulaire de tuple ou sous la forme curryfiée, la syntaxe de déclaration et d’assignation du délégué est un peu différente.</span><span class="sxs-lookup"><span data-stu-id="40791-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="40791-123">Le code suivant illustre quelques-unes des différentes façons dont vous pouvez travailler avec les délégués.</span><span class="sxs-lookup"><span data-stu-id="40791-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="40791-124">La sortie de l’exemple de code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="40791-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="40791-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40791-125">See also</span></span>

- [<span data-ttu-id="40791-126">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="40791-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="40791-127">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="40791-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="40791-128">Événements</span><span class="sxs-lookup"><span data-stu-id="40791-128">Events</span></span>](./members/events.md)
