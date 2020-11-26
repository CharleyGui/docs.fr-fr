---
description: ':::no-loc text=interface::: (Référence C#)'
title: interface - Référence C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89134586"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="bb31e-103">:::no-loc text="interface"::: (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="bb31e-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="bb31e-104">Une interface définit un contrat.</span><span class="sxs-lookup"><span data-stu-id="bb31e-104">An interface defines a contract.</span></span> <span data-ttu-id="bb31e-105">Tout [`class`](class.md) ou [`struct`](../builtin-types/struct.md) qui implémente ce contrat doit fournir une implémentation des membres définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="bb31e-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="bb31e-106">À compter de C# 8,0, une interface peut définir une implémentation par défaut pour les membres.</span><span class="sxs-lookup"><span data-stu-id="bb31e-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="bb31e-107">Il peut également définir des membres afin de [`static`](static.md) fournir une implémentation unique pour les fonctionnalités communes.</span><span class="sxs-lookup"><span data-stu-id="bb31e-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="bb31e-108">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="bb31e-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="bb31e-109">Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb31e-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb31e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb31e-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="bb31e-111">Une interface peut être membre d’un espace de noms ou d’une classe.</span><span class="sxs-lookup"><span data-stu-id="bb31e-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="bb31e-112">Une déclaration d’interface peut contenir des déclarations (signatures sans implémentation) des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="bb31e-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="bb31e-113">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bb31e-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="bb31e-114">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bb31e-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="bb31e-115">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="bb31e-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="bb31e-116">Événements</span><span class="sxs-lookup"><span data-stu-id="bb31e-116">Events</span></span>](event.md)

<span data-ttu-id="bb31e-117">Les déclarations de membre précédentes ne contiennent généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="bb31e-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="bb31e-118">À compter de C# 8,0, un membre d’interface peut déclarer un corps.</span><span class="sxs-lookup"><span data-stu-id="bb31e-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="bb31e-119">C’est ce qu’on appelle une *implémentation par défaut*.</span><span class="sxs-lookup"><span data-stu-id="bb31e-119">This is called a *default implementation*.</span></span> <span data-ttu-id="bb31e-120">Les membres avec des corps permettent à l’interface de fournir une implémentation « par défaut » pour les classes et les structs qui ne fournissent pas d’implémentation de substitution.</span><span class="sxs-lookup"><span data-stu-id="bb31e-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="bb31e-121">En outre, à compter de C# 8,0, une interface peut inclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="bb31e-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="bb31e-122">Constantes</span><span class="sxs-lookup"><span data-stu-id="bb31e-122">Constants</span></span>](const.md)
- [<span data-ttu-id="bb31e-123">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="bb31e-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="bb31e-124">[Constructeur statique](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="bb31e-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="bb31e-125">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="bb31e-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="bb31e-126">Champs, méthodes, propriétés, indexeurs et événements statiques</span><span class="sxs-lookup"><span data-stu-id="bb31e-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="bb31e-127">Déclarations de membre à l’aide de la syntaxe d’implémentation d’interface explicite.</span><span class="sxs-lookup"><span data-stu-id="bb31e-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="bb31e-128">Modificateurs d’accès explicites (l’accès par défaut est [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="bb31e-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="bb31e-129">Les interfaces ne peuvent pas contenir l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="bb31e-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="bb31e-130">Alors que les champs statiques sont désormais autorisés, les champs d’instance ne sont pas autorisés dans les interfaces.</span><span class="sxs-lookup"><span data-stu-id="bb31e-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="bb31e-131">Les [propriétés auto des instances](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ne sont pas prises en charge dans les interfaces, car elles déclarent implicitement un champ masqué.</span><span class="sxs-lookup"><span data-stu-id="bb31e-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="bb31e-132">Cette règle a un effet subtil sur les déclarations de propriété.</span><span class="sxs-lookup"><span data-stu-id="bb31e-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="bb31e-133">Dans une déclaration d’interface, le code suivant ne déclare pas une propriété implémentée automatiquement comme elle le fait dans un `class` ou un `struct` .</span><span class="sxs-lookup"><span data-stu-id="bb31e-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="bb31e-134">Au lieu de cela, elle déclare une propriété qui n’a pas d’implémentation par défaut, mais qui doit être implémentée dans tout type qui implémente l’interface :</span><span class="sxs-lookup"><span data-stu-id="bb31e-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="bb31e-135">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="bb31e-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="bb31e-136">Quand une interface [se substitue à une méthode](override.md) implémentée dans une interface de base, elle doit utiliser la syntaxe d' [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="bb31e-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="bb31e-137">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="bb31e-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="bb31e-138">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="bb31e-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="bb31e-139">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="bb31e-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="bb31e-140">En outre, les membres d’interface par défaut sont accessibles uniquement par le biais d’une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="bb31e-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="bb31e-141">Pour plus d’informations sur l’implémentation d’interface explicite, consultez [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="bb31e-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb31e-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb31e-142">Example</span></span>

<span data-ttu-id="bb31e-143">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="bb31e-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="bb31e-144">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="bb31e-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="bb31e-145">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="bb31e-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="bb31e-146">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="bb31e-146">C# language specification</span></span>

<span data-ttu-id="bb31e-147">Pour plus d’informations, consultez la section [interfaces](~/_csharplang/spec/interfaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md) et la spécification des fonctionnalités pour les [membres d’interface par défaut-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="bb31e-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="bb31e-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb31e-148">See also</span></span>

- [<span data-ttu-id="bb31e-149">Référence C#</span><span class="sxs-lookup"><span data-stu-id="bb31e-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb31e-150">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="bb31e-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb31e-151">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="bb31e-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bb31e-152">Types référence</span><span class="sxs-lookup"><span data-stu-id="bb31e-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="bb31e-153">Interfaces</span><span class="sxs-lookup"><span data-stu-id="bb31e-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="bb31e-154">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="bb31e-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="bb31e-155">Utilisation d'indexeurs</span><span class="sxs-lookup"><span data-stu-id="bb31e-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
