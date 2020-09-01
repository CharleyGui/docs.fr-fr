---
description: Limitations sur l’utilisation des niveaux d’accessibilité - Référence C#
title: Limitations sur l’utilisation des niveaux d’accessibilité - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 542e463e41c70f2e8aed5c20dc1294e296a88518
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136994"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="a2985-103">Limitations sur l’utilisation des niveaux d’accessibilité (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="a2985-103">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="a2985-104">Lorsque vous spécifiez un type dans une déclaration, vérifiez si le niveau d’accessibilité du type dépend du niveau d’accessibilité d’un membre ou d’un autre type.</span><span class="sxs-lookup"><span data-stu-id="a2985-104">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="a2985-105">Par exemple, la classe de base directe doit être au moins aussi accessible que la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="a2985-105">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="a2985-106">Les déclarations suivantes entraînent une erreur du compilateur, car la classe de base `BaseClass` est moins accessible que `MyClass` :</span><span class="sxs-lookup"><span data-stu-id="a2985-106">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="a2985-107">Le tableau suivant résume les limitations sur les niveaux d’accessibilité déclarés.</span><span class="sxs-lookup"><span data-stu-id="a2985-107">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="a2985-108">Context</span><span class="sxs-lookup"><span data-stu-id="a2985-108">Context</span></span>|<span data-ttu-id="a2985-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="a2985-109">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="a2985-110">Classes</span><span class="sxs-lookup"><span data-stu-id="a2985-110">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="a2985-111">La classe de base directe d’un type de classe doit être au moins aussi accessible que le type de classe lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-111">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="a2985-112">Interfaces</span><span class="sxs-lookup"><span data-stu-id="a2985-112">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="a2985-113">Les interfaces de base explicites d’un type d’interface doivent être au moins aussi accessibles que le type d’interface lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-113">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="a2985-114">Délégués</span><span class="sxs-lookup"><span data-stu-id="a2985-114">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="a2985-115">Le type de retour et les types de paramètres d’un type délégué doivent être au moins aussi accessibles que le type délégué lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-115">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="a2985-116">Constantes</span><span class="sxs-lookup"><span data-stu-id="a2985-116">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="a2985-117">Le type d’une constante doit être au moins aussi accessible que la constante elle-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-117">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="a2985-118">Fields</span><span class="sxs-lookup"><span data-stu-id="a2985-118">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="a2985-119">Le type d’un champ doit être au moins aussi accessible que le champ lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-119">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="a2985-120">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a2985-120">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="a2985-121">Le type de retour et les types de paramètres d’une méthode doivent être au moins aussi accessibles que la méthode elle-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-121">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="a2985-122">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a2985-122">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="a2985-123">Le type d’une propriété doit être au moins aussi accessible que la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-123">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="a2985-124">Événements</span><span class="sxs-lookup"><span data-stu-id="a2985-124">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="a2985-125">Le type d’un événement doit être au moins aussi accessible que l’événement lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-125">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="a2985-126">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="a2985-126">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="a2985-127">Le type et les types de paramètres d’un indexeur doivent être au moins aussi accessibles que l’indexeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-127">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="a2985-128">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="a2985-128">Operators</span></span>](../operators/index.md)|<span data-ttu-id="a2985-129">Le type de retour et les types de paramètres d’un opérateur doivent être au moins aussi accessibles que l’opérateur lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-129">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="a2985-130">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="a2985-130">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="a2985-131">Les types de paramètres d’un constructeur doivent être au moins aussi accessibles que le constructeur lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2985-131">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="a2985-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2985-132">Example</span></span>

<span data-ttu-id="a2985-133">L’exemple suivant contient des déclarations erronées de différents types.</span><span class="sxs-lookup"><span data-stu-id="a2985-133">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="a2985-134">Le commentaire qui suit chaque déclaration indique l’erreur du compilateur à attendre.</span><span class="sxs-lookup"><span data-stu-id="a2985-134">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="a2985-135">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a2985-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a2985-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2985-136">See also</span></span>

- [<span data-ttu-id="a2985-137">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a2985-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a2985-138">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a2985-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a2985-139">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a2985-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a2985-140">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="a2985-140">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="a2985-141">Domaine d’accessibilité</span><span class="sxs-lookup"><span data-stu-id="a2985-141">Accessibility Domain</span></span>](accessibility-domain.md)
- [<span data-ttu-id="a2985-142">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="a2985-142">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="a2985-143">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="a2985-143">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="a2985-144">public</span><span class="sxs-lookup"><span data-stu-id="a2985-144">public</span></span>](public.md)
- [<span data-ttu-id="a2985-145">priv</span><span class="sxs-lookup"><span data-stu-id="a2985-145">private</span></span>](private.md)
- [<span data-ttu-id="a2985-146">protected</span><span class="sxs-lookup"><span data-stu-id="a2985-146">protected</span></span>](protected.md)
- [<span data-ttu-id="a2985-147">intérieurs</span><span class="sxs-lookup"><span data-stu-id="a2985-147">internal</span></span>](internal.md)
