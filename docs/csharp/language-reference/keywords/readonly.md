---
title: readonly, mot clé - Référence C#
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: c3db8f7791e510768608e834339526fb82771979
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451939"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="63dd5-102">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="63dd5-102">readonly (C# Reference)</span></span>

<span data-ttu-id="63dd5-103">Le mot clé `readonly` est un modificateur qui peut être utilisé dans quatre contextes :</span><span class="sxs-lookup"><span data-stu-id="63dd5-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="63dd5-104">Dans une [déclaration de champ](#readonly-field-example), `readonly` indique qu’une affectation à destination d’un champ peut survenir uniquement dans le cadre de la déclaration ou dans un constructeur de la même classe.</span><span class="sxs-lookup"><span data-stu-id="63dd5-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="63dd5-105">Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.</span><span class="sxs-lookup"><span data-stu-id="63dd5-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="63dd5-106">Un champ `readonly` ne peut pas être assigné après la sortie du constructeur.</span><span class="sxs-lookup"><span data-stu-id="63dd5-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="63dd5-107">Cette règle a des implications différentes pour les types valeur et les types référence :</span><span class="sxs-lookup"><span data-stu-id="63dd5-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="63dd5-108">Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.</span><span class="sxs-lookup"><span data-stu-id="63dd5-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="63dd5-109">Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="63dd5-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="63dd5-110">Cet objet n’est pas immuable.</span><span class="sxs-lookup"><span data-stu-id="63dd5-110">That object isn't immutable.</span></span> <span data-ttu-id="63dd5-111">Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence.</span><span class="sxs-lookup"><span data-stu-id="63dd5-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="63dd5-112">Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du champ en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="63dd5-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="63dd5-113">Un type visible de l’extérieur qui contient un champ en lecture seule visible de l’extérieur qui est un type référence mutable peut être une faille de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « ne déclarez pas les types référence mutables en lecture seule ».</span><span class="sxs-lookup"><span data-stu-id="63dd5-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="63dd5-114">Dans une définition [`readonly struct`](#readonly-struct-example), `readonly` indique que le `struct` est immuable.</span><span class="sxs-lookup"><span data-stu-id="63dd5-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="63dd5-115">Dans une [définition de membre`readonly`](#readonly-member-examples), `readonly` indique qu’un membre d’un `struct` ne fait pas muter l’état interne de la structure.</span><span class="sxs-lookup"><span data-stu-id="63dd5-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="63dd5-116">Dans une [`ref readonly` méthode retournée](#ref-readonly-return-example), le modificateur `readonly` indique que la méthode retourne une référence et que les écritures ne sont pas autorisées dans cette référence.</span><span class="sxs-lookup"><span data-stu-id="63dd5-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="63dd5-117">Les contextes `readonly struct` et `ref readonly` ont été ajoutés C# dans 7,2.</span><span class="sxs-lookup"><span data-stu-id="63dd5-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="63dd5-118">`readonly` membres de struct ont été C# ajoutés dans 8,0</span><span class="sxs-lookup"><span data-stu-id="63dd5-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="63dd5-119">Exemple de champ en lecture seule</span><span class="sxs-lookup"><span data-stu-id="63dd5-119">Readonly field example</span></span>

<span data-ttu-id="63dd5-120">Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la `ChangeYear`de la méthode, même si une valeur lui est assignée dans le constructeur de classe :</span><span class="sxs-lookup"><span data-stu-id="63dd5-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="63dd5-121">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="63dd5-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="63dd5-122">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="63dd5-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="63dd5-123">Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="63dd5-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="63dd5-124">Dans le constructeur statique de la classe qui contient la déclaration de champ statique.</span><span class="sxs-lookup"><span data-stu-id="63dd5-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="63dd5-125">Ces contextes de constructeur sont également les seuls contextes dans lesquels il est possible de passer un champ `readonly` en tant que paramètre [out](out-parameter-modifier.md) ou [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="63dd5-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="63dd5-126">Le mot clé `readonly` est différent du mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="63dd5-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="63dd5-127">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="63dd5-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="63dd5-128">Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="63dd5-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="63dd5-129">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="63dd5-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="63dd5-130">De même, si un champ `const` est une constante de compilation, le champ `readonly` peut être utilisé pour les constantes Runtime, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="63dd5-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="63dd5-131">Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="63dd5-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="63dd5-132">vous obtiendrez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="63dd5-132">you'll get the compiler error message:</span></span>

<span data-ttu-id="63dd5-133">**Un champ ReadOnly ne peut pas être assigné (sauf s’il s’agit d’un constructeur ou d’un initialiseur de variable)**</span><span class="sxs-lookup"><span data-stu-id="63dd5-133">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-struct-example"></a><span data-ttu-id="63dd5-134">Exemple de struct readonly</span><span class="sxs-lookup"><span data-stu-id="63dd5-134">Readonly struct example</span></span>

<span data-ttu-id="63dd5-135">Le modificateur `readonly` dans une définition `struct` déclare que le struct est **immuable**.</span><span class="sxs-lookup"><span data-stu-id="63dd5-135">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="63dd5-136">Chaque champ d’instance du `struct` doit être marqué `readonly`, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="63dd5-136">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="63dd5-137">L’exemple précédent utilise les [propriétés automatiques readonly](../../properties.md#read-only) pour déclarer son stockage.</span><span class="sxs-lookup"><span data-stu-id="63dd5-137">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="63dd5-138">Il donne l’instruction au compilateur de créer des champs de stockage `readonly` pour ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="63dd5-138">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="63dd5-139">Vous pouvez aussi déclarer des champs `readonly` directement :</span><span class="sxs-lookup"><span data-stu-id="63dd5-139">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="63dd5-140">L’ajout d’un champ non marqué `readonly` génère l’erreur `CS8340` du compilateur : « Les champs d’instance de structs readonly doivent être en lecture seule ».</span><span class="sxs-lookup"><span data-stu-id="63dd5-140">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="63dd5-141">Exemples de membres ReadOnly</span><span class="sxs-lookup"><span data-stu-id="63dd5-141">Readonly member examples</span></span>

<span data-ttu-id="63dd5-142">Dans d’autres cas, vous pouvez créer un struct qui prend en charge la mutation.</span><span class="sxs-lookup"><span data-stu-id="63dd5-142">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="63dd5-143">Dans ces cas, plusieurs membres d’instance ne modifieront probablement pas l’état interne de la structure.</span><span class="sxs-lookup"><span data-stu-id="63dd5-143">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="63dd5-144">Vous pouvez déclarer ces membres d’instance avec le modificateur `readonly`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-144">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="63dd5-145">Le compilateur applique votre intention.</span><span class="sxs-lookup"><span data-stu-id="63dd5-145">The compiler enforces your intent.</span></span> <span data-ttu-id="63dd5-146">Si ce membre modifie l’État directement ou accède à un membre qui n’est pas également déclaré avec le modificateur `readonly`, le résultat est une erreur au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="63dd5-146">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="63dd5-147">Le modificateur de `readonly` est valide sur `struct` membres, et non sur les déclarations de membres `class` ou `interface`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-147">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="63dd5-148">Vous bénéficiez de deux avantages en appliquant le modificateur `readonly` aux méthodes `struct` applicables.</span><span class="sxs-lookup"><span data-stu-id="63dd5-148">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="63dd5-149">Plus important encore, le compilateur applique votre intention.</span><span class="sxs-lookup"><span data-stu-id="63dd5-149">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="63dd5-150">Le code qui modifie l’État n’est pas valide dans une méthode `readonly`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-150">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="63dd5-151">Le compilateur peut également utiliser le modificateur `readonly` pour activer les optimisations de performances.</span><span class="sxs-lookup"><span data-stu-id="63dd5-151">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="63dd5-152">Quand des types de `struct` volumineux sont passés par `in` référence, le compilateur doit générer une copie défensive si l’état de la structure peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="63dd5-152">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="63dd5-153">Si vous accédez uniquement à `readonly` membres, le compilateur ne peut pas créer la copie défensive.</span><span class="sxs-lookup"><span data-stu-id="63dd5-153">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="63dd5-154">Le modificateur de `readonly` est valide sur la plupart des membres d’un `struct`, y compris les méthodes qui substituent les méthodes déclarées dans <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63dd5-154">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="63dd5-155">Certaines restrictions s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="63dd5-155">There are some restrictions:</span></span>

- <span data-ttu-id="63dd5-156">Vous ne pouvez pas déclarer `readonly` des méthodes ou des propriétés statiques.</span><span class="sxs-lookup"><span data-stu-id="63dd5-156">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="63dd5-157">Vous ne pouvez pas déclarer des constructeurs `readonly`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-157">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="63dd5-158">Vous pouvez ajouter le modificateur `readonly` à une déclaration de propriété ou d’indexeur :</span><span class="sxs-lookup"><span data-stu-id="63dd5-158">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="63dd5-159">Vous pouvez également ajouter le modificateur `readonly` aux accesseurs individuels `get` ou `set` d’une propriété ou d’un indexeur :</span><span class="sxs-lookup"><span data-stu-id="63dd5-159">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="63dd5-160">Vous ne pouvez pas ajouter le modificateur `readonly` à la fois à une propriété et à un ou plusieurs des accesseurs de cette même propriété.</span><span class="sxs-lookup"><span data-stu-id="63dd5-160">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="63dd5-161">Cette même restriction s’applique aux indexeurs.</span><span class="sxs-lookup"><span data-stu-id="63dd5-161">That same restriction applies to indexers.</span></span>

<span data-ttu-id="63dd5-162">Le compilateur applique implicitement le modificateur `readonly` aux propriétés implémentées automatiquement où le code implémenté par le compilateur ne modifie pas l’État.</span><span class="sxs-lookup"><span data-stu-id="63dd5-162">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="63dd5-163">Elle est équivalente aux déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="63dd5-163">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="63dd5-164">Vous pouvez ajouter le modificateur `readonly` dans ces emplacements, mais il n’aura aucun effet significatif.</span><span class="sxs-lookup"><span data-stu-id="63dd5-164">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="63dd5-165">Vous ne pouvez pas ajouter le modificateur `readonly` à un accesseur Set de propriété implémentée automatiquement ou à une propriété implémentée automatiquement en lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="63dd5-165">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="63dd5-166">Exemple de retour ref readonly</span><span class="sxs-lookup"><span data-stu-id="63dd5-166">Ref readonly return example</span></span>

<span data-ttu-id="63dd5-167">Le modificateur `readonly` sur une `ref return` indique que la référence retournée ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="63dd5-167">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="63dd5-168">L’exemple suivant retourne une référence à l’origine.</span><span class="sxs-lookup"><span data-stu-id="63dd5-168">The following example returns a reference to the origin.</span></span> <span data-ttu-id="63dd5-169">Elle utilise le modificateur `readonly` pour indiquer que les appelants ne peuvent pas modifier l’origine :</span><span class="sxs-lookup"><span data-stu-id="63dd5-169">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="63dd5-170">Le type retourné ne doit pas nécessairement être un `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-170">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="63dd5-171">Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="63dd5-171">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="63dd5-172">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="63dd5-172">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="63dd5-173">Vous pouvez également consulter les propositions de spécification de langage :</span><span class="sxs-lookup"><span data-stu-id="63dd5-173">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="63dd5-174">ReadOnly et struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="63dd5-174">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="63dd5-175">membres de struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="63dd5-175">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="63dd5-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63dd5-176">See also</span></span>

- [<span data-ttu-id="63dd5-177">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="63dd5-177">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="63dd5-178">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="63dd5-178">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="63dd5-179">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="63dd5-179">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="63dd5-180">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="63dd5-180">Modifiers</span></span>](index.md)
- [<span data-ttu-id="63dd5-181">const</span><span class="sxs-lookup"><span data-stu-id="63dd5-181">const</span></span>](const.md)
- [<span data-ttu-id="63dd5-182">Fields</span><span class="sxs-lookup"><span data-stu-id="63dd5-182">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
