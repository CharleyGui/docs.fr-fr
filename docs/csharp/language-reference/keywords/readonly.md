---
title: readonly, mot clé - Référence C#
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345148"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="f55f7-102">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f55f7-102">readonly (C# Reference)</span></span>

<span data-ttu-id="f55f7-103">Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :</span><span class="sxs-lookup"><span data-stu-id="f55f7-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="f55f7-104">Dans une déclaration `readonly` de [terrain](#readonly-field-example), indique que l’affectation sur le terrain ne peut se produire que dans le cadre de la déclaration ou dans un constructeur dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="f55f7-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="f55f7-105">Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.</span><span class="sxs-lookup"><span data-stu-id="f55f7-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="f55f7-106">Un `readonly` champ ne peut pas être assigné après la sortie du constructeur.</span><span class="sxs-lookup"><span data-stu-id="f55f7-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="f55f7-107">Cette règle a des implications différentes pour les types de valeur et les types de référence :</span><span class="sxs-lookup"><span data-stu-id="f55f7-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="f55f7-108">Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.</span><span class="sxs-lookup"><span data-stu-id="f55f7-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="f55f7-109">Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="f55f7-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="f55f7-110">Cet objet n’est pas immuable.</span><span class="sxs-lookup"><span data-stu-id="f55f7-110">That object isn't immutable.</span></span> <span data-ttu-id="f55f7-111">Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence.</span><span class="sxs-lookup"><span data-stu-id="f55f7-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="f55f7-112">Toutefois, le modificateur n’empêche pas que les données d’instance du champ ne soient modifiées par le champ de lecture seulement.</span><span class="sxs-lookup"><span data-stu-id="f55f7-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="f55f7-113">Un type externement visible qui contient un champ de lecture-seulement visible à l’extérieur qui est un type de référence mutable peut être une vulnérabilité de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « Ne déclarez pas lu que les types de référence mutables. »</span><span class="sxs-lookup"><span data-stu-id="f55f7-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="f55f7-114">Dans `readonly struct` une définition `readonly` de type, indique que le type de structure est immuable.</span><span class="sxs-lookup"><span data-stu-id="f55f7-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="f55f7-115">Pour plus d’informations, consultez la [ `readonly` ](../builtin-types/struct.md#readonly-struct) section struct de l’article des types [structure.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="f55f7-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="f55f7-116">Dans [ `readonly` ](#readonly-member-examples)une définition `readonly` de membre , `struct` indique qu’un membre d’un ne mute pas l’état interne de la struct.</span><span class="sxs-lookup"><span data-stu-id="f55f7-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="f55f7-117">Dans [ `ref readonly` ](#ref-readonly-return-example)un retour `readonly` de méthode , le modificateur indique que la méthode renvoie une référence et écrit ne sont pas autorisés à cette référence.</span><span class="sxs-lookup"><span data-stu-id="f55f7-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="f55f7-118">Les `readonly struct` `ref readonly` contextes et les contextes ont été ajoutés dans C 7.2.</span><span class="sxs-lookup"><span data-stu-id="f55f7-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="f55f7-119">`readonly`membres struct ont été ajoutés dans C 8.0</span><span class="sxs-lookup"><span data-stu-id="f55f7-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="f55f7-120">Exemple de champ en lecture seule</span><span class="sxs-lookup"><span data-stu-id="f55f7-120">Readonly field example</span></span>

<span data-ttu-id="f55f7-121">Dans cet exemple, la `year` valeur du champ ne `ChangeYear`peut pas être changée dans la méthode, même si elle est attribuée une valeur dans le constructeur de classe:</span><span class="sxs-lookup"><span data-stu-id="f55f7-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="f55f7-122">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="f55f7-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="f55f7-123">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="f55f7-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="f55f7-124">Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="f55f7-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="f55f7-125">Dans le constructeur statique de la classe qui contient la déclaration de champ statique.</span><span class="sxs-lookup"><span data-stu-id="f55f7-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="f55f7-126">Ces contextes constructeurs sont également les seuls contextes dans `readonly` lesquels il est valable de passer un champ comme un paramètre [out](out-parameter-modifier.md) ou [ref.](ref.md)</span><span class="sxs-lookup"><span data-stu-id="f55f7-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="f55f7-127">Le mot clé `readonly` est différent du mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="f55f7-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="f55f7-128">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="f55f7-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="f55f7-129">Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="f55f7-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="f55f7-130">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="f55f7-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="f55f7-131">En outre, `const` alors qu’un champ est `readonly` une constante de compilateur- temps, le champ peut être employé pour des constantes de temps d’exécution comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f55f7-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="f55f7-132">Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="f55f7-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="f55f7-133">vous recevrez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="f55f7-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="f55f7-134">**Un champ de lecture ne peut pas être affecté à (sauf dans un constructeur ou un initialisateur variable)**</span><span class="sxs-lookup"><span data-stu-id="f55f7-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="f55f7-135">Exemples de membres Readonly</span><span class="sxs-lookup"><span data-stu-id="f55f7-135">Readonly member examples</span></span>

<span data-ttu-id="f55f7-136">D’autres fois, vous pouvez créer une struct qui soutient la mutation.</span><span class="sxs-lookup"><span data-stu-id="f55f7-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="f55f7-137">Dans ces cas, plusieurs des membres de l’instance ne modifieront probablement pas l’état interne de la struction.</span><span class="sxs-lookup"><span data-stu-id="f55f7-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="f55f7-138">Vous pouvez déclarer ces `readonly` membres d’instance avec le modificateur.</span><span class="sxs-lookup"><span data-stu-id="f55f7-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="f55f7-139">Le compilateur applique votre intention.</span><span class="sxs-lookup"><span data-stu-id="f55f7-139">The compiler enforces your intent.</span></span> <span data-ttu-id="f55f7-140">Si ce membre modifie directement l’état ou accède à `readonly` un membre qui n’est pas également déclaré avec le modificateur, le résultat est une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="f55f7-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="f55f7-141">Le `readonly` modificateur `struct` est valable `class` `interface` sur les membres, non ou les déclarations des membres.</span><span class="sxs-lookup"><span data-stu-id="f55f7-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="f55f7-142">Vous gagnez deux avantages `readonly` en appliquant le modificateur aux méthodes applicables. `struct`</span><span class="sxs-lookup"><span data-stu-id="f55f7-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="f55f7-143">Plus important encore, le compilateur applique votre intention.</span><span class="sxs-lookup"><span data-stu-id="f55f7-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="f55f7-144">Le code qui modifie l’état `readonly` n’est pas valide dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="f55f7-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="f55f7-145">Le compilateur peut également `readonly` utiliser le modificateur pour permettre des optimisations de performance.</span><span class="sxs-lookup"><span data-stu-id="f55f7-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="f55f7-146">Lorsque `struct` de grands `in` types sont adoptés par référence, le compilateur doit générer une copie défensive si l’état de la structe peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="f55f7-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="f55f7-147">Si `readonly` seulement les membres sont consultés, le compilateur ne peut pas créer la copie défensive.</span><span class="sxs-lookup"><span data-stu-id="f55f7-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="f55f7-148">Le `readonly` modificateur est valable `struct`sur la plupart des membres <xref:System.Object?displayProperty=nameWithType>d’un , y compris les méthodes qui remplacent les méthodes déclarées dans .</span><span class="sxs-lookup"><span data-stu-id="f55f7-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f55f7-149">Il y a quelques restrictions :</span><span class="sxs-lookup"><span data-stu-id="f55f7-149">There are some restrictions:</span></span>

- <span data-ttu-id="f55f7-150">Vous ne pouvez `readonly` pas déclarer des méthodes ou des propriétés statiques.</span><span class="sxs-lookup"><span data-stu-id="f55f7-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="f55f7-151">Vous ne pouvez `readonly` pas déclarer les constructeurs.</span><span class="sxs-lookup"><span data-stu-id="f55f7-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="f55f7-152">Vous pouvez `readonly` ajouter le modificateur à une déclaration de propriété ou d’indexeur :</span><span class="sxs-lookup"><span data-stu-id="f55f7-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="f55f7-153">Vous pouvez également `readonly` ajouter `get` le `set` modificateur à l’individu ou aux accesseurs d’une propriété ou d’un indexeur :</span><span class="sxs-lookup"><span data-stu-id="f55f7-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="f55f7-154">Vous ne pouvez `readonly` pas ajouter le modificateur à la fois à une propriété et à un ou plusieurs des accesseurs de cette même propriété.</span><span class="sxs-lookup"><span data-stu-id="f55f7-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="f55f7-155">Cette même restriction s’applique aux indexateurs.</span><span class="sxs-lookup"><span data-stu-id="f55f7-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="f55f7-156">Le compilateur applique `readonly` implicitement le modificateur aux propriétés auto-mises en œuvre où le code mis en œuvre par le compilateur ne modifie pas l’état.</span><span class="sxs-lookup"><span data-stu-id="f55f7-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="f55f7-157">C’est l’équivalent des déclarations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f55f7-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="f55f7-158">Vous pouvez `readonly` ajouter le modificateur dans ces endroits, mais il n’aura aucun effet significatif.</span><span class="sxs-lookup"><span data-stu-id="f55f7-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="f55f7-159">Vous ne pouvez `readonly` pas ajouter le modificateur à un setter de propriété auto-mis en œuvre, ou à une propriété mise en œuvre automatique de lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="f55f7-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="f55f7-160">Exemple de retour ref readonly</span><span class="sxs-lookup"><span data-stu-id="f55f7-160">Ref readonly return example</span></span>

<span data-ttu-id="f55f7-161">Le `readonly` modificateur `ref return` sur un indique que la référence retournée ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="f55f7-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="f55f7-162">L’exemple suivant retourne une référence à l’origine.</span><span class="sxs-lookup"><span data-stu-id="f55f7-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="f55f7-163">Il utilise `readonly` le modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :</span><span class="sxs-lookup"><span data-stu-id="f55f7-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="f55f7-164">Le type retourné ne doit pas nécessairement être un `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="f55f7-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="f55f7-165">Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="f55f7-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f55f7-166">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f55f7-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="f55f7-167">Vous pouvez également voir les propositions de spécification linguistique :</span><span class="sxs-lookup"><span data-stu-id="f55f7-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="f55f7-168">réajuster et structer readonly</span><span class="sxs-lookup"><span data-stu-id="f55f7-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="f55f7-169">rétructurer les membres</span><span class="sxs-lookup"><span data-stu-id="f55f7-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="f55f7-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f55f7-170">See also</span></span>

- [<span data-ttu-id="f55f7-171">Référence C</span><span class="sxs-lookup"><span data-stu-id="f55f7-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f55f7-172">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="f55f7-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f55f7-173">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="f55f7-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f55f7-174">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="f55f7-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f55f7-175">const</span><span class="sxs-lookup"><span data-stu-id="f55f7-175">const</span></span>](const.md)
- [<span data-ttu-id="f55f7-176">Champs</span><span class="sxs-lookup"><span data-stu-id="f55f7-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
