---
title: static, modificateur - Référence C#
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744662"
---
# <a name="static-c-reference"></a><span data-ttu-id="cf03a-102">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cf03a-102">static (C# Reference)</span></span>

<span data-ttu-id="cf03a-103">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="cf03a-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="cf03a-104">Le modificateur `static` peut être utilisé pour déclarer des classes `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-104">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="cf03a-105">Dans les classes, les interfaces et les structs, vous pouvez ajouter le modificateur `static` à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="cf03a-105">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="cf03a-106">Le modificateur `static` ne peut pas être utilisé avec des indexeurs ou des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="cf03a-106">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="cf03a-107">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="cf03a-107">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="cf03a-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf03a-108">Example</span></span>

<span data-ttu-id="cf03a-109">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="cf03a-109">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="cf03a-110">Une déclaration de constante ou de type est implicitement un membre `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-110">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="cf03a-111">Un membre `static` ne peut pas être référencé par le biais d’une instance.</span><span class="sxs-lookup"><span data-stu-id="cf03a-111">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="cf03a-112">Au lieu de cela, elle est référencée par le nom de type.</span><span class="sxs-lookup"><span data-stu-id="cf03a-112">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="cf03a-113">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="cf03a-113">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="cf03a-114">Pour faire référence au `x`membre `static`, utilisez le nom qualifié complet, `MyBaseC.MyStruct.x`, sauf si le membre est accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="cf03a-114">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="cf03a-115">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque champ `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-115">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="cf03a-116">Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des méthodes ou des accesseurs de propriété `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-116">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="cf03a-117">Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-117">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="cf03a-118">Les classes, les interfaces et les classes `static` peuvent avoir des constructeurs `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-118">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="cf03a-119">Un constructeur `static` est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="cf03a-119">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="cf03a-120">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="cf03a-120">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="cf03a-121">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="cf03a-121">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="cf03a-122">Pour illustrer `static` membres, considérons une classe qui représente un employé de la société.</span><span class="sxs-lookup"><span data-stu-id="cf03a-122">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="cf03a-123">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="cf03a-123">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="cf03a-124">La méthode et le champ n’appartiennent pas à une instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="cf03a-124">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="cf03a-125">Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="cf03a-125">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="cf03a-126">Ils doivent être déclarés comme `static` membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="cf03a-126">They should be declared as `static` members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="cf03a-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf03a-127">Example</span></span>

<span data-ttu-id="cf03a-128">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="cf03a-128">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="cf03a-129">Ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="cf03a-129">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="cf03a-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="cf03a-130">Example</span></span>

<span data-ttu-id="cf03a-131">Cet exemple montre que vous pouvez initialiser un champ `static` à l’aide d’un autre champ `static` qui n’est pas encore déclaré.</span><span class="sxs-lookup"><span data-stu-id="cf03a-131">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="cf03a-132">Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au champ `static`.</span><span class="sxs-lookup"><span data-stu-id="cf03a-132">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="cf03a-133">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cf03a-133">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cf03a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf03a-134">See also</span></span>

- [<span data-ttu-id="cf03a-135">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cf03a-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cf03a-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cf03a-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cf03a-137">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cf03a-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cf03a-138">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="cf03a-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="cf03a-139">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="cf03a-139">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
