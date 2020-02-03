---
title: interface - Référence C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: b315d1f04c9e74700afba8ee7871b23ab4b2fd28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744693"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="3f699-102">:::no-loc text="interface"::: (C# référence)</span><span class="sxs-lookup"><span data-stu-id="3f699-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="3f699-103">Une interface définit un contrat.</span><span class="sxs-lookup"><span data-stu-id="3f699-103">An interface defines a contract.</span></span> <span data-ttu-id="3f699-104">Tout [`class`](class.md) ou [`struct`](struct.md) qui implémente ce contrat doit fournir une implémentation des membres définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="3f699-104">Any [`class`](class.md) or [`struct`](struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="3f699-105">À partir C# de 8,0, une interface peut définir une implémentation par défaut pour les membres.</span><span class="sxs-lookup"><span data-stu-id="3f699-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="3f699-106">Elle peut également définir des membres de [`static`](static.md) pour fournir une implémentation unique pour les fonctionnalités communes.</span><span class="sxs-lookup"><span data-stu-id="3f699-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="3f699-107">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="3f699-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="3f699-108">Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="3f699-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="3f699-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f699-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="3f699-110">Une interface peut être membre d’un espace de noms ou d’une classe.</span><span class="sxs-lookup"><span data-stu-id="3f699-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="3f699-111">Une déclaration d’interface peut contenir des déclarations (signatures sans implémentation) des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="3f699-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="3f699-112">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f699-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="3f699-113">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3f699-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="3f699-114">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="3f699-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="3f699-115">Événements</span><span class="sxs-lookup"><span data-stu-id="3f699-115">Events</span></span>](event.md)

<span data-ttu-id="3f699-116">Les déclarations de membre précédentes ne contiennent généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="3f699-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="3f699-117">À partir C# de 8,0, un membre d’interface peut déclarer un corps.</span><span class="sxs-lookup"><span data-stu-id="3f699-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="3f699-118">C’est ce qu’on appelle une *implémentation par défaut*.</span><span class="sxs-lookup"><span data-stu-id="3f699-118">This is called a *default implementation*.</span></span> <span data-ttu-id="3f699-119">Les membres avec des corps permettent à l’interface de fournir une implémentation « par défaut » pour les classes et les structs qui ne fournissent pas d’implémentation de substitution.</span><span class="sxs-lookup"><span data-stu-id="3f699-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="3f699-120">En outre, à partir C# de 8,0, une interface peut inclure :</span><span class="sxs-lookup"><span data-stu-id="3f699-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="3f699-121">Constantes</span><span class="sxs-lookup"><span data-stu-id="3f699-121">Constants</span></span>](const.md)
- [<span data-ttu-id="3f699-122">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="3f699-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="3f699-123">[Constructeur statique](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="3f699-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="3f699-124">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="3f699-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="3f699-125">Champs, méthodes, propriétés, indexeurs et événements statiques</span><span class="sxs-lookup"><span data-stu-id="3f699-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="3f699-126">Déclarations de membre à l’aide de la syntaxe d’implémentation d’interface explicite.</span><span class="sxs-lookup"><span data-stu-id="3f699-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="3f699-127">Modificateurs d’accès explicites (l’accès par défaut est [`public`](access-modifiers.md)).</span><span class="sxs-lookup"><span data-stu-id="3f699-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="3f699-128">Les interfaces ne peuvent pas contenir l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="3f699-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="3f699-129">Alors que les champs statiques sont désormais autorisés, les champs d’instance ne sont pas autorisés dans les interfaces.</span><span class="sxs-lookup"><span data-stu-id="3f699-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="3f699-130">Les [propriétés auto des instances](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ne sont pas prises en charge dans les interfaces, car elles déclarent implicitement un champ masqué.</span><span class="sxs-lookup"><span data-stu-id="3f699-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="3f699-131">Cette règle a un effet subtil sur les déclarations de propriété.</span><span class="sxs-lookup"><span data-stu-id="3f699-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="3f699-132">Dans une déclaration d’interface, le code suivant ne déclare pas une propriété implémentée automatiquement telle qu’elle le fait dans un `class` ou `struct`.</span><span class="sxs-lookup"><span data-stu-id="3f699-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="3f699-133">Au lieu de cela, elle déclare une propriété qui n’a pas d’implémentation par défaut, mais qui doit être implémentée dans tout type qui implémente l’interface :</span><span class="sxs-lookup"><span data-stu-id="3f699-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="3f699-134">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="3f699-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="3f699-135">Quand une interface [se substitue à une méthode](override.md) implémentée dans une interface de base, elle doit utiliser la syntaxe d' [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="3f699-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="3f699-136">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="3f699-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="3f699-137">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="3f699-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="3f699-138">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="3f699-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="3f699-139">En outre, les membres d’interface par défaut sont accessibles uniquement par le biais d’une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="3f699-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="3f699-140">Pour plus d’informations sur l’implémentation d’interface explicite, consultez [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="3f699-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="3f699-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f699-141">Example</span></span>

<span data-ttu-id="3f699-142">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="3f699-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="3f699-143">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="3f699-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="3f699-144">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="3f699-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="3f699-145">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="3f699-145">C# language specification</span></span>

<span data-ttu-id="3f699-146">Pour plus d’informations, consultez la section [interfaces](~/_csharplang/spec/interfaces.md) de la [ C# spécification de langage](~/_csharplang/spec/introduction.md) et la spécification de fonctionnalité pour les membres d' [interface par défaut- C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="3f699-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="3f699-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f699-147">See also</span></span>

- [<span data-ttu-id="3f699-148">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="3f699-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f699-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="3f699-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f699-150">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="3f699-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3f699-151">Types référence</span><span class="sxs-lookup"><span data-stu-id="3f699-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="3f699-152">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3f699-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="3f699-153">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="3f699-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="3f699-154">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="3f699-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="3f699-155">class</span><span class="sxs-lookup"><span data-stu-id="3f699-155">class</span></span>](class.md)
- [<span data-ttu-id="3f699-156">struct</span><span class="sxs-lookup"><span data-stu-id="3f699-156">struct</span></span>](struct.md)
- [<span data-ttu-id="3f699-157">Interfaces</span><span class="sxs-lookup"><span data-stu-id="3f699-157">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
