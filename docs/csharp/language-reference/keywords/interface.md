---
title: interface - Référence C#
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 869f1398ae0af3c7379655aa018a9f4aacb934d7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243969"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="ac5ac-102">:::no-loc text="interface":::(Référence C#)</span><span class="sxs-lookup"><span data-stu-id="ac5ac-102">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="ac5ac-103">Une interface définit un contrat.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-103">An interface defines a contract.</span></span> <span data-ttu-id="ac5ac-104">Tout [`class`](class.md) ou [`struct`](../builtin-types/struct.md) qui implémente ce contrat doit fournir une implémentation des membres définis dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-104">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="ac5ac-105">À compter de C# 8,0, une interface peut définir une implémentation par défaut pour les membres.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-105">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="ac5ac-106">Il peut également définir des membres afin de [`static`](static.md) fournir une implémentation unique pour les fonctionnalités communes.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-106">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="ac5ac-107">Dans l’exemple suivant, la classe `ImplementationClass` doit implémenter une méthode nommée `SampleMethod` qui n’a aucun paramètre et qui retourne `void`.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-107">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="ac5ac-108">Pour plus d’informations et d’exemples, consultez [Interfaces](../../programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="ac5ac-108">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="ac5ac-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac5ac-109">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="ac5ac-110">Une interface peut être membre d’un espace de noms ou d’une classe.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-110">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="ac5ac-111">Une déclaration d’interface peut contenir des déclarations (signatures sans implémentation) des membres suivants :</span><span class="sxs-lookup"><span data-stu-id="ac5ac-111">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="ac5ac-112">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ac5ac-112">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="ac5ac-113">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ac5ac-113">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="ac5ac-114">Indexeurs</span><span class="sxs-lookup"><span data-stu-id="ac5ac-114">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="ac5ac-115">Événements</span><span class="sxs-lookup"><span data-stu-id="ac5ac-115">Events</span></span>](event.md)

<span data-ttu-id="ac5ac-116">Les déclarations de membre précédentes ne contiennent généralement pas de corps.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-116">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="ac5ac-117">À compter de C# 8,0, un membre d’interface peut déclarer un corps.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-117">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="ac5ac-118">C’est ce qu’on appelle une *implémentation par défaut*.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-118">This is called a *default implementation*.</span></span> <span data-ttu-id="ac5ac-119">Les membres avec des corps permettent à l’interface de fournir une implémentation « par défaut » pour les classes et les structs qui ne fournissent pas d’implémentation de substitution.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-119">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="ac5ac-120">En outre, à compter de C# 8,0, une interface peut inclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ac5ac-120">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="ac5ac-121">Constantes</span><span class="sxs-lookup"><span data-stu-id="ac5ac-121">Constants</span></span>](const.md)
- [<span data-ttu-id="ac5ac-122">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="ac5ac-122">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="ac5ac-123">[Constructeur statique](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="ac5ac-123">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="ac5ac-124">Types imbriqués</span><span class="sxs-lookup"><span data-stu-id="ac5ac-124">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="ac5ac-125">Champs, méthodes, propriétés, indexeurs et événements statiques</span><span class="sxs-lookup"><span data-stu-id="ac5ac-125">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="ac5ac-126">Déclarations de membre à l’aide de la syntaxe d’implémentation d’interface explicite.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-126">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="ac5ac-127">Modificateurs d’accès explicites (l’accès par défaut est [`public`](access-modifiers.md) ).</span><span class="sxs-lookup"><span data-stu-id="ac5ac-127">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="ac5ac-128">Les interfaces ne peuvent pas contenir l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-128">Interfaces may not contain instance state.</span></span> <span data-ttu-id="ac5ac-129">Alors que les champs statiques sont désormais autorisés, les champs d’instance ne sont pas autorisés dans les interfaces.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-129">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="ac5ac-130">Les [propriétés auto des instances](../../programming-guide/classes-and-structs/auto-implemented-properties.md) ne sont pas prises en charge dans les interfaces, car elles déclarent implicitement un champ masqué.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-130">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="ac5ac-131">Cette règle a un effet subtil sur les déclarations de propriété.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-131">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="ac5ac-132">Dans une déclaration d’interface, le code suivant ne déclare pas une propriété implémentée automatiquement comme elle le fait dans un `class` ou un `struct` .</span><span class="sxs-lookup"><span data-stu-id="ac5ac-132">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="ac5ac-133">Au lieu de cela, elle déclare une propriété qui n’a pas d’implémentation par défaut, mais qui doit être implémentée dans tout type qui implémente l’interface :</span><span class="sxs-lookup"><span data-stu-id="ac5ac-133">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="ac5ac-134">Une interface peut hériter d’une ou de plusieurs interfaces de base.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-134">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="ac5ac-135">Quand une interface [se substitue à une méthode](override.md) implémentée dans une interface de base, elle doit utiliser la syntaxe d' [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md) .</span><span class="sxs-lookup"><span data-stu-id="ac5ac-135">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="ac5ac-136">Lorsqu’une liste de types de base contient une classe de base et des interfaces, la classe de base doit figurer en premier dans la liste.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-136">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="ac5ac-137">Une classe qui implémente une interface peut implémenter explicitement les membres de cette interface.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-137">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="ac5ac-138">Un membre implémenté explicitement n’est pas accessible via une instance de classe, mais uniquement via une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-138">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="ac5ac-139">En outre, les membres d’interface par défaut sont accessibles uniquement par le biais d’une instance de l’interface.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-139">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="ac5ac-140">Pour plus d’informations sur l’implémentation d’interface explicite, consultez [implémentation d’interface explicite](../../programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="ac5ac-140">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="ac5ac-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac5ac-141">Example</span></span>

<span data-ttu-id="ac5ac-142">L’exemple suivant montre une implémentation d’interface.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-142">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="ac5ac-143">Dans cet exemple, l’interface contient la déclaration de propriété, et la classe contient l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-143">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="ac5ac-144">Toutes les instances d’une classe qui implémentent `IPoint` ont les propriétés entières `x` et `y`.</span><span class="sxs-lookup"><span data-stu-id="ac5ac-144">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="ac5ac-145">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ac5ac-145">C# language specification</span></span>

<span data-ttu-id="ac5ac-146">Pour plus d’informations, consultez la section [interfaces](~/_csharplang/spec/interfaces.md) de la [spécification du langage C#](~/_csharplang/spec/introduction.md) et la spécification des fonctionnalités pour les [membres d’interface par défaut-C# 8,0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span><span class="sxs-lookup"><span data-stu-id="ac5ac-146">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="ac5ac-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac5ac-147">See also</span></span>

- [<span data-ttu-id="ac5ac-148">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ac5ac-148">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ac5ac-149">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ac5ac-149">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ac5ac-150">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="ac5ac-150">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ac5ac-151">Types référence</span><span class="sxs-lookup"><span data-stu-id="ac5ac-151">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="ac5ac-152">Interfaces</span><span class="sxs-lookup"><span data-stu-id="ac5ac-152">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="ac5ac-153">Utilisation de propriétés</span><span class="sxs-lookup"><span data-stu-id="ac5ac-153">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="ac5ac-154">Utilisation d'indexeurs</span><span class="sxs-lookup"><span data-stu-id="ac5ac-154">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
