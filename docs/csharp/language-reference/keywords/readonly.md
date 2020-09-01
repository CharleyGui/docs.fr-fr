---
description: readonly, mot clé - Référence C#
title: readonly, mot clé - Référence C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b1bab5af18216fcef2162179493dbbb59e3470cf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137173"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="31436-103">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="31436-103">readonly (C# Reference)</span></span>

<span data-ttu-id="31436-104">Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :</span><span class="sxs-lookup"><span data-stu-id="31436-104">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="31436-105">Dans une [déclaration de champ](#readonly-field-example), `readonly` indique que l’assignation au champ peut uniquement se produire dans le cadre de la déclaration ou dans un constructeur de la même classe.</span><span class="sxs-lookup"><span data-stu-id="31436-105">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="31436-106">Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.</span><span class="sxs-lookup"><span data-stu-id="31436-106">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="31436-107">Un `readonly` champ ne peut pas être assigné après la sortie du constructeur.</span><span class="sxs-lookup"><span data-stu-id="31436-107">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="31436-108">Cette règle a des implications différentes pour les types valeur et les types référence :</span><span class="sxs-lookup"><span data-stu-id="31436-108">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="31436-109">Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.</span><span class="sxs-lookup"><span data-stu-id="31436-109">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="31436-110">Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="31436-110">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="31436-111">Cet objet n’est pas immuable.</span><span class="sxs-lookup"><span data-stu-id="31436-111">That object isn't immutable.</span></span> <span data-ttu-id="31436-112">Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence.</span><span class="sxs-lookup"><span data-stu-id="31436-112">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="31436-113">Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du champ en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="31436-113">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="31436-114">Un type visible de l’extérieur qui contient un champ en lecture seule visible de l’extérieur qui est un type référence mutable peut être une faille de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « ne déclarez pas les types référence mutables en lecture seule ».</span><span class="sxs-lookup"><span data-stu-id="31436-114">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="31436-115">Dans une `readonly struct` définition de type, `readonly` indique que le type de structure est immuable.</span><span class="sxs-lookup"><span data-stu-id="31436-115">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="31436-116">Pour plus d’informations, consultez la section [ `readonly` struct](../builtin-types/struct.md#readonly-struct) de l’article [types de structures](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="31436-116">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="31436-117">Dans une déclaration de membre d’instance au sein d’un type structure, `readonly` indique qu’un membre d’instance ne modifie pas l’état de la structure.</span><span class="sxs-lookup"><span data-stu-id="31436-117">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="31436-118">Pour plus d’informations, consultez la section [ `readonly` membres d’instance](../builtin-types/struct.md#readonly-instance-members) de l’article [types de structures](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="31436-118">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="31436-119">Dans une [ `ref readonly` méthode retournée](#ref-readonly-return-example), le `readonly` modificateur indique que la méthode retourne une référence et que les écritures ne sont pas autorisées à cette référence.</span><span class="sxs-lookup"><span data-stu-id="31436-119">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="31436-120">Les `readonly struct` `ref readonly` contextes et ont été ajoutés en C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="31436-120">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="31436-121">`readonly` des membres de struct ont été ajoutés en C# 8,0</span><span class="sxs-lookup"><span data-stu-id="31436-121">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="31436-122">Exemple de champ en lecture seule</span><span class="sxs-lookup"><span data-stu-id="31436-122">Readonly field example</span></span>

<span data-ttu-id="31436-123">Dans cet exemple, la valeur du champ `year` ne peut pas être modifiée dans la méthode `ChangeYear` , même si une valeur lui est assignée dans le constructeur de classe :</span><span class="sxs-lookup"><span data-stu-id="31436-123">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="31436-124">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="31436-124">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="31436-125">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="31436-125">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="31436-126">Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="31436-126">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="31436-127">Dans le constructeur statique de la classe qui contient la déclaration de champ statique.</span><span class="sxs-lookup"><span data-stu-id="31436-127">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="31436-128">Ces contextes de constructeur sont également les seuls contextes dans lesquels il est possible de passer un `readonly` champ en tant que paramètre [out](out-parameter-modifier.md) ou [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="31436-128">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="31436-129">Le mot clé `readonly` est différent du mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="31436-129">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="31436-130">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="31436-130">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="31436-131">Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="31436-131">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="31436-132">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="31436-132">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="31436-133">De même, si un `const` champ est une constante de compilation, le `readonly` champ peut être utilisé pour les constantes Runtime, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="31436-133">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="31436-134">Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="31436-134">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="31436-135">vous obtiendrez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="31436-135">you'll get the compiler error message:</span></span>

<span data-ttu-id="31436-136">**Un champ ReadOnly ne peut pas être assigné (sauf s’il s’agit d’un constructeur ou d’un initialiseur de variable)**</span><span class="sxs-lookup"><span data-stu-id="31436-136">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="31436-137">Exemple de retour ref readonly</span><span class="sxs-lookup"><span data-stu-id="31436-137">Ref readonly return example</span></span>

<span data-ttu-id="31436-138">Le `readonly` modificateur sur un `ref return` indique que la référence retournée ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="31436-138">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="31436-139">L’exemple suivant retourne une référence à l’origine.</span><span class="sxs-lookup"><span data-stu-id="31436-139">The following example returns a reference to the origin.</span></span> <span data-ttu-id="31436-140">Elle utilise le `readonly` modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :</span><span class="sxs-lookup"><span data-stu-id="31436-140">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="31436-141">Le type retourné ne doit pas nécessairement être un `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="31436-141">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="31436-142">Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="31436-142">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="31436-143">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="31436-143">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="31436-144">Vous pouvez également consulter les propositions de spécification de langage :</span><span class="sxs-lookup"><span data-stu-id="31436-144">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="31436-145">ReadOnly et struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="31436-145">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="31436-146">membres de struct ReadOnly</span><span class="sxs-lookup"><span data-stu-id="31436-146">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="31436-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31436-147">See also</span></span>

- [<span data-ttu-id="31436-148">Référence C#</span><span class="sxs-lookup"><span data-stu-id="31436-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31436-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="31436-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31436-150">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="31436-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31436-151">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="31436-151">Modifiers</span></span>](index.md)
- [<span data-ttu-id="31436-152">const</span><span class="sxs-lookup"><span data-stu-id="31436-152">const</span></span>](const.md)
- [<span data-ttu-id="31436-153">Fields</span><span class="sxs-lookup"><span data-stu-id="31436-153">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
