---
description: static, modificateur - Référence C#
title: static, modificateur - Référence C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: f42636d1bbdf4342297f46f50ec6dfc2a70eacad
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142061"
---
# <a name="static-c-reference"></a><span data-ttu-id="5559d-103">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="5559d-103">static (C# Reference)</span></span>

<span data-ttu-id="5559d-104">Cette page couvre le `static` mot clé de modificateur.</span><span class="sxs-lookup"><span data-stu-id="5559d-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="5559d-105">Le `static` mot clé fait également partie de la [`using static`](using-static.md) directive.</span><span class="sxs-lookup"><span data-stu-id="5559d-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="5559d-106">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="5559d-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="5559d-107">Le `static` modificateur peut être utilisé pour déclarer des `static` classes.</span><span class="sxs-lookup"><span data-stu-id="5559d-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="5559d-108">Dans les classes, les interfaces et les structs, vous pouvez ajouter le `static` modificateur à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="5559d-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="5559d-109">Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="5559d-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="5559d-110">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="5559d-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="5559d-111">Exemple : classe statique</span><span class="sxs-lookup"><span data-stu-id="5559d-111">Example - static class</span></span>

<span data-ttu-id="5559d-112">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="5559d-112">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="5559d-113">Une déclaration de constante ou de type est implicitement un `static` membre.</span><span class="sxs-lookup"><span data-stu-id="5559d-113">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="5559d-114">Un `static` membre ne peut pas être référencé par le biais d’une instance.</span><span class="sxs-lookup"><span data-stu-id="5559d-114">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="5559d-115">Au lieu de cela, elle est référencée par le nom de type.</span><span class="sxs-lookup"><span data-stu-id="5559d-115">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="5559d-116">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="5559d-116">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="5559d-117">Pour faire référence au `static` membre `x` , utilisez le nom qualifié complet, `MyBaseC.MyStruct.x` , sauf si le membre est accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="5559d-117">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="5559d-118">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque `static` champ.</span><span class="sxs-lookup"><span data-stu-id="5559d-118">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="5559d-119">Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des `static` méthodes ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="5559d-119">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="5559d-120">Si le `static` mot clé est appliqué à une classe, tous les membres de la classe doivent avoir la valeur `static` .</span><span class="sxs-lookup"><span data-stu-id="5559d-120">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="5559d-121">Les classes, les interfaces et les `static` classes peuvent avoir des `static` constructeurs.</span><span class="sxs-lookup"><span data-stu-id="5559d-121">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="5559d-122">Un `static` constructeur est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="5559d-122">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="5559d-123">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="5559d-123">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="5559d-124">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="5559d-124">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="5559d-125">Pour illustrer `static` les membres, considérez une classe qui représente un employé de la société.</span><span class="sxs-lookup"><span data-stu-id="5559d-125">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="5559d-126">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="5559d-126">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="5559d-127">La méthode et le champ n’appartiennent pas à une instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="5559d-127">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="5559d-128">Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="5559d-128">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="5559d-129">Ils doivent être déclarés en tant que `static` membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="5559d-129">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="5559d-130">Exemple : champ et méthode statiques</span><span class="sxs-lookup"><span data-stu-id="5559d-130">Example - static field and method</span></span>

<span data-ttu-id="5559d-131">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="5559d-131">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="5559d-132">Ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="5559d-132">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="5559d-133">Exemple : initialisation statique</span><span class="sxs-lookup"><span data-stu-id="5559d-133">Example - static initialization</span></span>

<span data-ttu-id="5559d-134">Cet exemple montre que vous pouvez initialiser un `static` champ à l’aide d’un autre `static` champ qui n’est pas encore déclaré.</span><span class="sxs-lookup"><span data-stu-id="5559d-134">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="5559d-135">Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au `static` champ.</span><span class="sxs-lookup"><span data-stu-id="5559d-135">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="5559d-136">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="5559d-136">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5559d-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5559d-137">See also</span></span>

- [<span data-ttu-id="5559d-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="5559d-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5559d-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5559d-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5559d-140">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="5559d-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5559d-141">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="5559d-141">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5559d-142">using static, directive</span><span class="sxs-lookup"><span data-stu-id="5559d-142">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="5559d-143">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="5559d-143">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
