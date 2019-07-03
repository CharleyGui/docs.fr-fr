---
title: readonly, mot clé - Référence C#
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348008"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="71f1c-102">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="71f1c-102">readonly (C# Reference)</span></span>

<span data-ttu-id="71f1c-103">Le mot clé `readonly` est un modificateur qui peut être utilisé dans trois contextes :</span><span class="sxs-lookup"><span data-stu-id="71f1c-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="71f1c-104">Dans une [déclaration de champ](#readonly-field-example), `readonly` indique qu’une affectation à destination d’un champ peut survenir uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe.</span><span class="sxs-lookup"><span data-stu-id="71f1c-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="71f1c-105">Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.</span><span class="sxs-lookup"><span data-stu-id="71f1c-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="71f1c-106">Un champ `readonly` ne peut pas être affecté après l’arrêt du constructeur.</span><span class="sxs-lookup"><span data-stu-id="71f1c-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="71f1c-107">Cela a des implications différentes selon les types de valeur et les types de référence :</span><span class="sxs-lookup"><span data-stu-id="71f1c-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="71f1c-108">Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.</span><span class="sxs-lookup"><span data-stu-id="71f1c-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="71f1c-109">Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="71f1c-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="71f1c-110">Cet objet n’est pas immuable.</span><span class="sxs-lookup"><span data-stu-id="71f1c-110">That object is not immutable.</span></span> <span data-ttu-id="71f1c-111">Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence.</span><span class="sxs-lookup"><span data-stu-id="71f1c-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="71f1c-112">Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le champ en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="71f1c-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="71f1c-113">Un type visible de l’extérieur qui contient un champ en lecture seule visible de l’extérieur qui est un type de référence mutable peut être une faille de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : « Ne déclarez pas les types référence mutables en lecture seule »</span><span class="sxs-lookup"><span data-stu-id="71f1c-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="71f1c-114">Dans une définition [`readonly struct`](#readonly-struct-example), `readonly` indique que le `struct` est immuable.</span><span class="sxs-lookup"><span data-stu-id="71f1c-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="71f1c-115">Dans un [`ref readonly`retour de la méthode](#ref-readonly-return-example), le modificateur `readonly` indique que la méthode retourne une référence et que les écritures ne sont pas autorisés pour cette référence.</span><span class="sxs-lookup"><span data-stu-id="71f1c-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="71f1c-116">Les deux contextes finaux ont été ajoutés dans C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="71f1c-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="71f1c-117">Exemple de champ en lecture seule</span><span class="sxs-lookup"><span data-stu-id="71f1c-117">Readonly field example</span></span>

<span data-ttu-id="71f1c-118">Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear`, même si une valeur lui est affectée dans le constructeur de classe :</span><span class="sxs-lookup"><span data-stu-id="71f1c-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="71f1c-119">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="71f1c-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="71f1c-120">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="71f1c-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="71f1c-121">Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="71f1c-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="71f1c-122">Dans le constructeur statique de la classe qui contient la déclaration de champ statique.</span><span class="sxs-lookup"><span data-stu-id="71f1c-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="71f1c-123">Ces contextes de constructeur sont aussi les seuls contextes dans lesquels il est possible de passer un champ `readonly` comme paramètre [out](out-parameter-modifier.md) ou [ref](ref.md).</span><span class="sxs-lookup"><span data-stu-id="71f1c-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="71f1c-124">Le mot clé `readonly` est différent du mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="71f1c-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="71f1c-125">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="71f1c-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="71f1c-126">Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="71f1c-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="71f1c-127">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="71f1c-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="71f1c-128">De même, alors qu’un champ `const` est une constante au moment de la compilation, le champ `readonly` peut être utilisé pour des constantes au moment de l’exécution, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71f1c-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="71f1c-129">Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71f1c-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="71f1c-130">vous obtenez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="71f1c-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="71f1c-131">Exemple de struct readonly</span><span class="sxs-lookup"><span data-stu-id="71f1c-131">Readonly struct example</span></span>

<span data-ttu-id="71f1c-132">Le modificateur `readonly` dans une définition `struct` déclare que le struct est **immuable**.</span><span class="sxs-lookup"><span data-stu-id="71f1c-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="71f1c-133">Chaque champ d’instance du `struct` doit être marqué `readonly`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71f1c-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="71f1c-134">L’exemple précédent utilise les [propriétés automatiques readonly](../../properties.md#read-only) pour déclarer son stockage.</span><span class="sxs-lookup"><span data-stu-id="71f1c-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="71f1c-135">Il donne l’instruction au compilateur de créer des champs de stockage `readonly` pour ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="71f1c-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="71f1c-136">Vous pouvez aussi déclarer des champs `readonly` directement :</span><span class="sxs-lookup"><span data-stu-id="71f1c-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="71f1c-137">L’ajout d’un champ non marqué `readonly` génère l’erreur du compilateur `CS8340` : « Les champs d’instance de structs en lecture seule doivent être en lecture seule. »</span><span class="sxs-lookup"><span data-stu-id="71f1c-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="71f1c-138">Exemple de retour ref readonly</span><span class="sxs-lookup"><span data-stu-id="71f1c-138">Ref readonly return example</span></span>

<span data-ttu-id="71f1c-139">Le modificateur `readonly` au niveau d’un `ref return` indique que la référence retournée ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="71f1c-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="71f1c-140">L’exemple suivant retourne une référence à l’origine.</span><span class="sxs-lookup"><span data-stu-id="71f1c-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="71f1c-141">Il utilise le modificateur `readonly` pour indiquer que les appelants ne peuvent pas modifier l’origine :</span><span class="sxs-lookup"><span data-stu-id="71f1c-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="71f1c-142">Le type retourné ne doit pas nécessairement être un `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="71f1c-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="71f1c-143">Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="71f1c-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="71f1c-144">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="71f1c-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="71f1c-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71f1c-145">See also</span></span>

- [<span data-ttu-id="71f1c-146">Référence C#</span><span class="sxs-lookup"><span data-stu-id="71f1c-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="71f1c-147">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="71f1c-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="71f1c-148">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="71f1c-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="71f1c-149">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="71f1c-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="71f1c-150">const</span><span class="sxs-lookup"><span data-stu-id="71f1c-150">const</span></span>](const.md)
- [<span data-ttu-id="71f1c-151">Champs</span><span class="sxs-lookup"><span data-stu-id="71f1c-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
