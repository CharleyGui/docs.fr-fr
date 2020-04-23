---
title: static, modificateur - Référence C#
ms.date: 04/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 771bcfdac4c4bf27c15da4bc374d804405317a78
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102058"
---
# <a name="static-c-reference"></a><span data-ttu-id="98a66-102">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="98a66-102">static (C# Reference)</span></span>

<span data-ttu-id="98a66-103">Cette page `static` couvre le mot clé modificateur.</span><span class="sxs-lookup"><span data-stu-id="98a66-103">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="98a66-104">Le `static` mot clé fait [`using static`](using-static.md) également partie de la directive.</span><span class="sxs-lookup"><span data-stu-id="98a66-104">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="98a66-105">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="98a66-105">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="98a66-106">Le `static` modificateur peut `static` être utilisé pour déclarer les cours.</span><span class="sxs-lookup"><span data-stu-id="98a66-106">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="98a66-107">Dans les classes, les interfaces et les `static` structs, vous pouvez ajouter le modificateur aux champs, méthodes, propriétés, opérateurs, événements et constructeurs.</span><span class="sxs-lookup"><span data-stu-id="98a66-107">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="98a66-108">Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finalisateurs.</span><span class="sxs-lookup"><span data-stu-id="98a66-108">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="98a66-109">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="98a66-109">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example---static-class"></a><span data-ttu-id="98a66-110">Exemple - classe statique</span><span class="sxs-lookup"><span data-stu-id="98a66-110">Example - static class</span></span>

<span data-ttu-id="98a66-111">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="98a66-111">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="98a66-112">Une déclaration constante ou type `static` est implicitement un membre.</span><span class="sxs-lookup"><span data-stu-id="98a66-112">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="98a66-113">Un `static` membre ne peut pas être référencé par une instance.</span><span class="sxs-lookup"><span data-stu-id="98a66-113">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="98a66-114">Au lieu de cela, il est référencé à travers le nom de type.</span><span class="sxs-lookup"><span data-stu-id="98a66-114">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="98a66-115">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="98a66-115">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="98a66-116">Pour se `static` référer `x`au membre, utilisez `MyBaseC.MyStruct.x`le nom entièrement qualifié, à moins que le membre ne soit accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="98a66-116">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="98a66-117">Bien qu’une instance d’une classe contient une copie distincte de tous `static` les champs d’instance de la classe, il n’y a qu’une seule copie de chaque champ.</span><span class="sxs-lookup"><span data-stu-id="98a66-117">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="98a66-118">Il n’est pas [`this`](this.md) possible `static` d’utiliser pour référencer les méthodes ou les accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="98a66-118">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="98a66-119">Si `static` le mot clé est appliqué à une classe, tous les membres de la classe doivent être `static`.</span><span class="sxs-lookup"><span data-stu-id="98a66-119">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="98a66-120">Les classes, les `static` interfaces `static` et les classes peuvent avoir des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="98a66-120">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="98a66-121">Un `static` constructeur est appelé à un moment donné entre le moment où le programme commence et la classe est instantanée.</span><span class="sxs-lookup"><span data-stu-id="98a66-121">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="98a66-122">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="98a66-122">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="98a66-123">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="98a66-123">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="98a66-124">Pour `static` démontrer aux membres, considérez une classe qui représente un employé de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="98a66-124">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="98a66-125">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="98a66-125">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="98a66-126">La méthode et le terrain n’appartiennent à aucun cas d’employé.</span><span class="sxs-lookup"><span data-stu-id="98a66-126">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="98a66-127">Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="98a66-127">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="98a66-128">Ils doivent être `static` déclarés membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="98a66-128">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="98a66-129">Exemple - champ statique et méthode</span><span class="sxs-lookup"><span data-stu-id="98a66-129">Example - static field and method</span></span>

<span data-ttu-id="98a66-130">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="98a66-130">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="98a66-131">Ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="98a66-131">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="98a66-132">Exemple - initialisation statique</span><span class="sxs-lookup"><span data-stu-id="98a66-132">Example - static initialization</span></span>

<span data-ttu-id="98a66-133">Cet exemple montre que vous `static` pouvez initialiser un champ en utilisant un autre `static` champ qui n’est pas encore déclaré.</span><span class="sxs-lookup"><span data-stu-id="98a66-133">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="98a66-134">Les résultats ne seront pas définis jusqu’à `static` ce que vous affectiez explicitement une valeur sur le terrain.</span><span class="sxs-lookup"><span data-stu-id="98a66-134">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="98a66-135">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="98a66-135">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="98a66-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98a66-136">See also</span></span>

- [<span data-ttu-id="98a66-137">Référence C</span><span class="sxs-lookup"><span data-stu-id="98a66-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98a66-138">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="98a66-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98a66-139">Mots-clés C</span><span class="sxs-lookup"><span data-stu-id="98a66-139">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98a66-140">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="98a66-140">Modifiers</span></span>](index.md)
- [<span data-ttu-id="98a66-141">en utilisant une directive statique</span><span class="sxs-lookup"><span data-stu-id="98a66-141">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="98a66-142">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="98a66-142">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
