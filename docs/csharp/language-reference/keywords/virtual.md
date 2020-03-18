---
title: virtual - Référence C#
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173456"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="159d4-102">virtual (référence C#)</span><span class="sxs-lookup"><span data-stu-id="159d4-102">virtual (C# Reference)</span></span>

<span data-ttu-id="159d4-103">Le mot clé `virtual` sert à modifier une méthode, une propriété, un indexeur ou une déclaration event et leur permet d’être substitués dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="159d4-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="159d4-104">Par exemple, cette méthode peut être substituée par toute classe qui en hérite :</span><span class="sxs-lookup"><span data-stu-id="159d4-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="159d4-105">L’implémentation d’un membre virtuel peut être modifiée par un [membre de substitution](override.md) dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="159d4-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="159d4-106">Pour plus d’informations `virtual` sur la façon d’utiliser le mot clé, voir [Version avec le remplacement et les nouveaux mots clés](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et savoir quand utiliser Le remplacement et les nouveaux mots [clés](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="159d4-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="159d4-107">Notes </span><span class="sxs-lookup"><span data-stu-id="159d4-107">Remarks</span></span>

<span data-ttu-id="159d4-108">Quand une méthode virtuelle est appelée, un membre de substitution est recherché dans le type d’objet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="159d4-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="159d4-109">Le membre de substitution de la classe la plus dérivée est appelé (cela peut être le membre d’origine), si aucune classe dérivée n’a substitué le membre.</span><span class="sxs-lookup"><span data-stu-id="159d4-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="159d4-110">Par défaut, les méthodes ne sont pas virtuelles.</span><span class="sxs-lookup"><span data-stu-id="159d4-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="159d4-111">Vous ne pouvez pas substituer une méthode non virtuelle.</span><span class="sxs-lookup"><span data-stu-id="159d4-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="159d4-112">Vous ne pouvez pas utiliser le modificateur `virtual` avec les modificateurs `static`, `abstract`, `private` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="159d4-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="159d4-113">L’exemple suivant illustre une propriété virtuelle :</span><span class="sxs-lookup"><span data-stu-id="159d4-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="159d4-114">Les propriétés virtuelles se comportent comme des méthodes virtuelles, à l’exception des différences de déclaration et de syntaxe d’invocation.</span><span class="sxs-lookup"><span data-stu-id="159d4-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="159d4-115">L’utilisation du modificateur `virtual` sur une propriété statique serait une erreur.</span><span class="sxs-lookup"><span data-stu-id="159d4-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="159d4-116">Une propriété virtuelle héritée peut être substituée dans une classe dérivée en incluant une déclaration de propriété qui utilise le modificateur `override`.</span><span class="sxs-lookup"><span data-stu-id="159d4-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="159d4-117"> Exemple</span><span class="sxs-lookup"><span data-stu-id="159d4-117">Example</span></span>

<span data-ttu-id="159d4-118">Dans cet exemple, la classe `Shape` contient les deux coordonnées `x` et `y`, ainsi que la méthode virtuelle `Area()`.</span><span class="sxs-lookup"><span data-stu-id="159d4-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="159d4-119">Différentes classes de formes, telles que `Circle`, `Cylinder` et `Sphere`, héritent de la classe `Shape`, et la surface est calculée pour chaque figure.</span><span class="sxs-lookup"><span data-stu-id="159d4-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="159d4-120">Chaque classe dérivée a sa propre implémentation de substitution de `Area()`.</span><span class="sxs-lookup"><span data-stu-id="159d4-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="159d4-121">Notez que les classes héritées `Circle`, `Sphere` et `Cylinder` utilisent toutes des constructeurs qui initialisent la classe de base, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="159d4-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="159d4-122">Le programme suivant calcule et affiche la zone appropriée pour chaque figure en appelant l’implémentation appropriée de la méthode `Area()`, selon l’objet associé à la méthode.</span><span class="sxs-lookup"><span data-stu-id="159d4-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="159d4-123">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="159d4-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="159d4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="159d4-124">See also</span></span>

- [<span data-ttu-id="159d4-125">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="159d4-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="159d4-126">Abstrait</span><span class="sxs-lookup"><span data-stu-id="159d4-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="159d4-127">Substituer</span><span class="sxs-lookup"><span data-stu-id="159d4-127">override</span></span>](override.md)
- [<span data-ttu-id="159d4-128">new (modificateur)</span><span class="sxs-lookup"><span data-stu-id="159d4-128">new (modifier)</span></span>](new-modifier.md)
