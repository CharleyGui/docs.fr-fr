---
title: Types énumération - Guide de programmation C#
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3573959a1e10b475a9867631767de5d10a08b9ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969774"
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="ae831-102">Types énumération (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ae831-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="ae831-103">Un type énumération (également appelé énumération ou enum) offre un moyen efficace de définir un ensemble de constantes intégrales nommées qui peuvent être assignées à une variable.</span><span class="sxs-lookup"><span data-stu-id="ae831-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="ae831-104">Par exemple, supposez que vous devez définir une variable dont la valeur représente un jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="ae831-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="ae831-105">Il n’y a que sept valeurs significatives qui pourront être stockées par cette variable.</span><span class="sxs-lookup"><span data-stu-id="ae831-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="ae831-106">Pour définir ces valeurs, vous pouvez utiliser un type énumération, qui est déclaré à l’aide du mot clé [enum](../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="ae831-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="ae831-107">Par défaut, le type sous-jacent de chaque élément dans l’énumération est [int](../language-reference/builtin-types/integral-numeric-types.md). Vous pouvez spécifier un autre type numérique intégral à l’aide d’un signe deux-points, comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="ae831-107">By default the underlying type of each element in the enum is [int](../language-reference/builtin-types/integral-numeric-types.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="ae831-108">Pour obtenir une liste complète des types possibles, consultez [enum (référence C#)](../language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="ae831-108">For a full list of possible types, see [enum (C# Reference)](../language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="ae831-109">Vous pouvez vérifier les valeurs numériques sous-jacentes en effectuant un cast sur le type sous-jacent, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ae831-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="ae831-110">Voici les avantages qu’offre l’utilisation d’un enum par rapport à un type numérique :</span><span class="sxs-lookup"><span data-stu-id="ae831-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="ae831-111">Vous spécifiez clairement pour le code client les valeurs qui sont valides pour la variable.</span><span class="sxs-lookup"><span data-stu-id="ae831-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="ae831-112">Dans Visual Studio, IntelliSense liste les valeurs définies.</span><span class="sxs-lookup"><span data-stu-id="ae831-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="ae831-113">Quand vous ne spécifiez pas de valeurs pour les éléments dans la liste d’énumérateurs, les valeurs sont automatiquement incrémentées de 1.</span><span class="sxs-lookup"><span data-stu-id="ae831-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="ae831-114">Dans l’exemple précédent, `Day.Sunday` a la valeur 0, `Day.Monday` a la valeur 1 et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="ae831-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="ae831-115">Quand vous créez un objet `Day`, il a la valeur par défaut `Day.Sunday` (0) si vous ne lui assignez pas une valeur explicitement.</span><span class="sxs-lookup"><span data-stu-id="ae831-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="ae831-116">Quand vous créez un enum, sélectionnez la valeur par défaut la plus logique et affectez-lui une valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="ae831-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="ae831-117">Ainsi, tous les enums auront cette valeur par défaut si aucune valeur ne leur est assignée explicitement lors de leur création.</span><span class="sxs-lookup"><span data-stu-id="ae831-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="ae831-118">Si la variable `meetingDay` est de type `Day`, alors (sans un cast explicite) vous pouvez uniquement lui affecter l’une des valeurs définies par `Day`.</span><span class="sxs-lookup"><span data-stu-id="ae831-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="ae831-119">Si le jour de la réunion change, vous pouvez affecter une nouvelle valeur de `Day` à `meetingDay` :</span><span class="sxs-lookup"><span data-stu-id="ae831-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="ae831-120">Il est possible d’assigner une valeur entière arbitraire à `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="ae831-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="ae831-121">Par exemple, cette ligne de code ne produit pas d’erreur : `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="ae831-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="ae831-122">Toutefois, vous ne devez pas le faire car l’attente implicite est qu’une variable enum ne contiendra que l’une des valeurs définies par l’enum.</span><span class="sxs-lookup"><span data-stu-id="ae831-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="ae831-123">Affecter une valeur arbitraire à une variable de type énumération présente un risque élevé d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ae831-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="ae831-124">Vous pouvez affecter n’importe quelle valeur aux éléments dans la liste d’énumérateurs d’un type énumération, et vous pouvez également utiliser des valeurs calculées :</span><span class="sxs-lookup"><span data-stu-id="ae831-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="ae831-125">Types énumération comme indicateurs binaires</span><span class="sxs-lookup"><span data-stu-id="ae831-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="ae831-126">Vous pouvez utiliser un type énumération pour définir des indicateurs binaires, ce qui permet à une instance du type énumération de stocker n’importe quelle combinaison des valeurs définies dans la liste d’énumérateurs.</span><span class="sxs-lookup"><span data-stu-id="ae831-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="ae831-127">(Bien entendu, certaines combinaisons peuvent ne pas être significatives ou autorisées dans votre code de programme.)</span><span class="sxs-lookup"><span data-stu-id="ae831-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="ae831-128">Pour créer un enum d’indicateurs binaires, vous devez appliquer l’attribut <xref:System.FlagsAttribute?displayProperty=nameWithType> et définir les valeurs de manière appropriée afin que les opérations au niveau du bit `AND`, `OR`, `NOT` et `XOR` puissent être effectuées sur elles.</span><span class="sxs-lookup"><span data-stu-id="ae831-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="ae831-129">Dans l’enum d’indicateurs binaires, incluez une constante nommée avec une valeur zéro qui signifie « aucun indicateur n’est défini. »</span><span class="sxs-lookup"><span data-stu-id="ae831-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="ae831-130">N’attribuez pas la valeur zéro à un indicateur si cela ne signifie pas « aucun indicateur n’est défini ».</span><span class="sxs-lookup"><span data-stu-id="ae831-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="ae831-131">Dans l’exemple suivant, une autre version de l’enum `Day`, nommée `Days`, est définie.</span><span class="sxs-lookup"><span data-stu-id="ae831-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="ae831-132">`Days` a l’attribut `Flags`, et à chaque valeur est affectée la puissance de deux supérieure suivante.</span><span class="sxs-lookup"><span data-stu-id="ae831-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="ae831-133">Cela vous permet de créer une variable `Days` dont la valeur est `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="ae831-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="ae831-134">Pour définir un indicateur sur un enum, utilisez l’opérateur binaire `OR` comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ae831-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="ae831-135">Pour déterminer si un indicateur spécifique est défini, utilisez une opération `AND` au niveau du bit, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ae831-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="ae831-136">Pour plus d’informations sur les éléments à prendre en compte quand vous définissez des types énumération avec l’attribut <xref:System.FlagsAttribute?displayProperty=nameWithType>, consultez <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae831-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="ae831-137">Utilisation des méthodes System.Enum pour découvrir et manipuler des valeurs enum</span><span class="sxs-lookup"><span data-stu-id="ae831-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="ae831-138">Tous les enums sont des instances du type <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae831-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="ae831-139">Vous ne pouvez pas dériver de nouvelles classes à partir de <xref:System.Enum?displayProperty=nameWithType>, mais vous pouvez utiliser ses méthodes pour découvrir des informations et manipuler les valeurs d’une instance enum.</span><span class="sxs-lookup"><span data-stu-id="ae831-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="ae831-140">Pour plus d'informations, consultez <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ae831-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ae831-141">Vous pouvez également créer une méthode pour un enum à l’aide d’une méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="ae831-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="ae831-142">Pour plus d’informations, consultez [comment créer une nouvelle méthode pour une énumération](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ae831-142">For more information, see [How to create a new method for an enumeration](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae831-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae831-143">See also</span></span>

- <xref:System.Enum?displayProperty=nameWithType>
- [<span data-ttu-id="ae831-144">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ae831-144">C# Programming Guide</span></span>](./index.md)
- [<span data-ttu-id="ae831-145">enum</span><span class="sxs-lookup"><span data-stu-id="ae831-145">enum</span></span>](../language-reference/keywords/enum.md)
