---
title: readonly, mot clé - Référence C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389055"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="ea27c-102">readonly (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ea27c-102">readonly (C# Reference)</span></span>

<span data-ttu-id="ea27c-103">Le `readonly` mot clé est un modificateur qui peut être utilisé dans quatre contextes :</span><span class="sxs-lookup"><span data-stu-id="ea27c-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="ea27c-104">Dans une déclaration `readonly` de [terrain](#readonly-field-example), indique que l’affectation sur le terrain ne peut se produire que dans le cadre de la déclaration ou dans un constructeur dans la même classe.</span><span class="sxs-lookup"><span data-stu-id="ea27c-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="ea27c-105">Un champ en lecture seule peut être affecté et réaffecté plusieurs fois dans la déclaration de champ et le constructeur.</span><span class="sxs-lookup"><span data-stu-id="ea27c-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="ea27c-106">Un `readonly` champ ne peut pas être assigné après la sortie du constructeur.</span><span class="sxs-lookup"><span data-stu-id="ea27c-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="ea27c-107">Cette règle a des implications différentes pour les types de valeur et les types de référence :</span><span class="sxs-lookup"><span data-stu-id="ea27c-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="ea27c-108">Étant donné que les types de valeur contiennent directement leurs données, un champ qui est un type de valeur `readonly` est immuable.</span><span class="sxs-lookup"><span data-stu-id="ea27c-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="ea27c-109">Étant donné que les types de référence contiennent une référence à leurs données, un champ qui est un type de référence `readonly` doit toujours faire référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="ea27c-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="ea27c-110">Cet objet n’est pas immuable.</span><span class="sxs-lookup"><span data-stu-id="ea27c-110">That object isn't immutable.</span></span> <span data-ttu-id="ea27c-111">Le modificateur `readonly` empêche le champ d’être remplacé par une autre instance du type de référence.</span><span class="sxs-lookup"><span data-stu-id="ea27c-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="ea27c-112">Toutefois, le modificateur n’empêche pas que les données d’instance du champ ne soient modifiées par le champ de lecture seulement.</span><span class="sxs-lookup"><span data-stu-id="ea27c-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="ea27c-113">Un type externement visible qui contient un champ de lecture-seulement visible à l’extérieur qui est un type de référence mutable peut être une vulnérabilité de sécurité et peut déclencher l’avertissement [CA2104](/visualstudio/code-quality/ca2104) : « Ne déclarez pas lu que les types de référence mutables. »</span><span class="sxs-lookup"><span data-stu-id="ea27c-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="ea27c-114">Dans `readonly struct` une définition `readonly` de type, indique que le type de structure est immuable.</span><span class="sxs-lookup"><span data-stu-id="ea27c-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="ea27c-115">Pour plus d’informations, consultez la [ `readonly` ](../builtin-types/struct.md#readonly-struct) section struct de l’article des types [structure.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="ea27c-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="ea27c-116">Dans une déclaration de membre `readonly` dans un type de structure, indique qu’un membre de l’instance ne modifie pas l’état de la structure.</span><span class="sxs-lookup"><span data-stu-id="ea27c-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="ea27c-117">Pour plus d’informations, consultez la [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) section des membres d’instance de l’article [de type Structure.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="ea27c-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="ea27c-118">Dans [ `ref readonly` ](#ref-readonly-return-example)un retour `readonly` de méthode , le modificateur indique que la méthode renvoie une référence et écrit ne sont pas autorisés à cette référence.</span><span class="sxs-lookup"><span data-stu-id="ea27c-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="ea27c-119">Les `readonly struct` `ref readonly` contextes et les contextes ont été ajoutés dans C 7.2.</span><span class="sxs-lookup"><span data-stu-id="ea27c-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="ea27c-120">`readonly`membres struct ont été ajoutés dans C 8.0</span><span class="sxs-lookup"><span data-stu-id="ea27c-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="ea27c-121">Exemple de champ en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ea27c-121">Readonly field example</span></span>

<span data-ttu-id="ea27c-122">Dans cet exemple, la `year` valeur du champ ne `ChangeYear`peut pas être changée dans la méthode, même si elle est attribuée une valeur dans le constructeur de classe:</span><span class="sxs-lookup"><span data-stu-id="ea27c-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="ea27c-123">Vous pouvez affecter une valeur à un champ `readonly` uniquement dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="ea27c-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="ea27c-124">Lorsque la variable est initialisée dans la déclaration, par exemple :</span><span class="sxs-lookup"><span data-stu-id="ea27c-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="ea27c-125">Dans un constructeur d’instance de la classe qui contient la déclaration de champ d’instance.</span><span class="sxs-lookup"><span data-stu-id="ea27c-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="ea27c-126">Dans le constructeur statique de la classe qui contient la déclaration de champ statique.</span><span class="sxs-lookup"><span data-stu-id="ea27c-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="ea27c-127">Ces contextes constructeurs sont également les seuls contextes dans `readonly` lesquels il est valable de passer un champ comme un paramètre [out](out-parameter-modifier.md) ou [ref.](ref.md)</span><span class="sxs-lookup"><span data-stu-id="ea27c-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="ea27c-128">Le mot clé `readonly` est différent du mot clé [const](const.md).</span><span class="sxs-lookup"><span data-stu-id="ea27c-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="ea27c-129">Un champ `const` ne peut être initialisé qu'au moment de la déclaration du champ.</span><span class="sxs-lookup"><span data-stu-id="ea27c-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="ea27c-130">Un champ `readonly` peut être assigné plusieurs fois dans la déclaration de champ et dans un constructeur.</span><span class="sxs-lookup"><span data-stu-id="ea27c-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="ea27c-131">C'est pourquoi, les champs `readonly` peuvent avoir des valeurs différentes en fonction du constructeur utilisé.</span><span class="sxs-lookup"><span data-stu-id="ea27c-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="ea27c-132">En outre, `const` alors qu’un champ est `readonly` une constante de compilateur- temps, le champ peut être employé pour des constantes de temps d’exécution comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ea27c-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="ea27c-133">Dans l’exemple précédent, si vous utilisez une instruction telle que dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ea27c-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="ea27c-134">vous recevrez le message d’erreur du compilateur :</span><span class="sxs-lookup"><span data-stu-id="ea27c-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="ea27c-135">**Un champ de lecture ne peut pas être affecté à (sauf dans un constructeur ou un initialisateur variable)**</span><span class="sxs-lookup"><span data-stu-id="ea27c-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="ea27c-136">Exemple de retour ref readonly</span><span class="sxs-lookup"><span data-stu-id="ea27c-136">Ref readonly return example</span></span>

<span data-ttu-id="ea27c-137">Le `readonly` modificateur `ref return` sur un indique que la référence retournée ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="ea27c-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="ea27c-138">L’exemple suivant retourne une référence à l’origine.</span><span class="sxs-lookup"><span data-stu-id="ea27c-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="ea27c-139">Il utilise `readonly` le modificateur pour indiquer que les appelants ne peuvent pas modifier l’origine :</span><span class="sxs-lookup"><span data-stu-id="ea27c-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="ea27c-140">Le type retourné ne doit pas nécessairement être un `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="ea27c-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="ea27c-141">Tout type pouvant être retourné par `ref` peut être retourné par `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="ea27c-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ea27c-142">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ea27c-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="ea27c-143">Vous pouvez également voir les propositions de spécification linguistique :</span><span class="sxs-lookup"><span data-stu-id="ea27c-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="ea27c-144">réajuster et structer readonly</span><span class="sxs-lookup"><span data-stu-id="ea27c-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="ea27c-145">rétructurer les membres</span><span class="sxs-lookup"><span data-stu-id="ea27c-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="ea27c-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea27c-146">See also</span></span>

- [<span data-ttu-id="ea27c-147">Référence C</span><span class="sxs-lookup"><span data-stu-id="ea27c-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ea27c-148">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="ea27c-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ea27c-149">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="ea27c-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ea27c-150">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="ea27c-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ea27c-151">const</span><span class="sxs-lookup"><span data-stu-id="ea27c-151">const</span></span>](const.md)
- [<span data-ttu-id="ea27c-152">Fields</span><span class="sxs-lookup"><span data-stu-id="ea27c-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
