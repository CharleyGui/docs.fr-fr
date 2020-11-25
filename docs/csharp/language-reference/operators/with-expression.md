---
title: avec expression-référence C#
description: En savoir plus sur une expression with qui effectue une mutation non destructrice d’enregistrements C#
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: d7d3758c8c5da7859974b5b50b63d2a5ca16b24d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702223"
---
# <a name="with-expression-c-reference"></a><span data-ttu-id="536d1-103">with, expression (référence C#)</span><span class="sxs-lookup"><span data-stu-id="536d1-103">with expression (C# reference)</span></span>

<span data-ttu-id="536d1-104">Disponible en C# 9,0 et versions ultérieures, une `with` expression génère une copie de son opérande [Record](../../whats-new/csharp-9.md#record-types) avec les propriétés et les champs spécifiés modifiés :</span><span class="sxs-lookup"><span data-stu-id="536d1-104">Available in C# 9.0 and later, a `with` expression produces a copy of its [record](../../whats-new/csharp-9.md#record-types) operand with the specified properties and fields modified:</span></span>

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

<span data-ttu-id="536d1-105">Comme le montre l’exemple précédent, vous utilisez la syntaxe de l' [initialiseur d’objet](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) pour spécifier les membres à modifier et leurs nouvelles valeurs.</span><span class="sxs-lookup"><span data-stu-id="536d1-105">As the preceding example shows, you use [object initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) syntax to specify what members to modify and their new values.</span></span> <span data-ttu-id="536d1-106">Dans une `with` expression, un opérande de gauche doit être d’un type d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="536d1-106">In a `with` expression, a left-hand operand must be of a record type.</span></span>

<span data-ttu-id="536d1-107">Le résultat d’une `with` expression a le même type au moment de l’exécution que l’opérande de l’expression, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="536d1-107">The result of a `with` expression has the same runtime type as the expression's operand, as the following example shows:</span></span>

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

<span data-ttu-id="536d1-108">Dans le cas d’un membre de type référence, seule la référence à une instance est copiée lors de la copie d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="536d1-108">In the case of a reference-type member, only the reference to an instance is copied when a record is copied.</span></span> <span data-ttu-id="536d1-109">La copie et l’enregistrement d’origine ont accès à la même instance de type référence.</span><span class="sxs-lookup"><span data-stu-id="536d1-109">Both the copy and original record have access to the same reference-type instance.</span></span> <span data-ttu-id="536d1-110">L’exemple suivant illustre ce comportement :</span><span class="sxs-lookup"><span data-stu-id="536d1-110">The following example demonstrates that behavior:</span></span>

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

<span data-ttu-id="536d1-111">Tout type d’enregistrement a le *constructeur de copie*.</span><span class="sxs-lookup"><span data-stu-id="536d1-111">Any record type has the *copy constructor*.</span></span> <span data-ttu-id="536d1-112">Il s’agit d’un constructeur avec un paramètre unique du type d’enregistrement contenant.</span><span class="sxs-lookup"><span data-stu-id="536d1-112">That is a constructor with a single parameter of the containing record type.</span></span> <span data-ttu-id="536d1-113">Elle copie l’état de son argument dans une nouvelle instance d’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="536d1-113">It copies the state of its argument to a new record instance.</span></span> <span data-ttu-id="536d1-114">Lors de l’évaluation d’une `with` expression, le constructeur de copie est appelé pour instancier une nouvelle instance d’enregistrement basée sur un enregistrement d’origine.</span><span class="sxs-lookup"><span data-stu-id="536d1-114">At evaluation of a `with` expression, the copy constructor gets called to instantiate a new record instance based on an original record.</span></span> <span data-ttu-id="536d1-115">Après cela, la nouvelle instance est mise à jour selon les modifications spécifiées.</span><span class="sxs-lookup"><span data-stu-id="536d1-115">After that, the new instance gets updated according to the specified modifications.</span></span> <span data-ttu-id="536d1-116">Par défaut, le constructeur de copie est implicite, c’est-à-dire qu’il est généré par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="536d1-116">By default, the copy constructor is implicit, that is, compiler-generated.</span></span> <span data-ttu-id="536d1-117">Si vous devez personnaliser la sémantique de copie des enregistrements, déclarez explicitement un constructeur de copie avec le comportement souhaité.</span><span class="sxs-lookup"><span data-stu-id="536d1-117">If you need to customize the record copy semantics, explicitly declare a copy constructor with the desired behavior.</span></span> <span data-ttu-id="536d1-118">L’exemple suivant met à jour l’exemple précédent avec un constructeur de copie explicite.</span><span class="sxs-lookup"><span data-stu-id="536d1-118">The following example updates the preceding example with an explicit copy constructor.</span></span> <span data-ttu-id="536d1-119">Le nouveau comportement de copie consiste à copier des éléments de liste au lieu d’une référence de liste lorsqu’un enregistrement est copié :</span><span class="sxs-lookup"><span data-stu-id="536d1-119">The new copy behavior is to copy list items instead of a list reference when a record is copied:</span></span>

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a><span data-ttu-id="536d1-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="536d1-120">C# language specification</span></span>

<span data-ttu-id="536d1-121">Pour plus d’informations, consultez les sections suivantes de la [proposition de fonctionnalité d’enregistrements note](~/_csharplang/proposals/csharp-9.0/records.md):</span><span class="sxs-lookup"><span data-stu-id="536d1-121">For more information, see the following sections of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md):</span></span>

- [<span data-ttu-id="536d1-122">`with` formule</span><span class="sxs-lookup"><span data-stu-id="536d1-122">`with` expression</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [<span data-ttu-id="536d1-123">Copier et cloner des membres</span><span class="sxs-lookup"><span data-stu-id="536d1-123">Copy and Clone members</span></span>](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a><span data-ttu-id="536d1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="536d1-124">See also</span></span>

- [<span data-ttu-id="536d1-125">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="536d1-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="536d1-126">Opérateurs et expressions C#</span><span class="sxs-lookup"><span data-stu-id="536d1-126">C# operators and expressions</span></span>](index.md)
