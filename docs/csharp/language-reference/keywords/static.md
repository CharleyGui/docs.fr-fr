---
title: static, modificateur - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: cbd0f6b4ef7976ccc2da2a735ccbba2bf23177e4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422333"
---
# <a name="static-c-reference"></a><span data-ttu-id="64478-102">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="64478-102">static (C# Reference)</span></span>

<span data-ttu-id="64478-103">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="64478-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="64478-104">Le modificateur `static` peut être utilisé avec des classes, des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs. En revanche, il ne peut pas être utilisé avec des indexeurs, des finaliseurs ni des types autres que des classes.</span><span class="sxs-lookup"><span data-stu-id="64478-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="64478-105">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="64478-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="64478-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="64478-106">Example</span></span>

<span data-ttu-id="64478-107">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="64478-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="64478-108">Une déclaration de constante ou de type est implicitement un membre statique.</span><span class="sxs-lookup"><span data-stu-id="64478-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="64478-109">Un membre statique ne peut pas être référencé via une instance.</span><span class="sxs-lookup"><span data-stu-id="64478-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="64478-110">Au lieu de cela, il est référencé via le nom de type.</span><span class="sxs-lookup"><span data-stu-id="64478-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="64478-111">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="64478-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="64478-112">Pour faire référence au membre statique `x`, utilisez le nom complet `MyBaseC.MyStruct.x`, à moins que le membre soit accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="64478-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="64478-113">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il existe une seule copie de chaque champ statique.</span><span class="sxs-lookup"><span data-stu-id="64478-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="64478-114">Il n’est pas possible d’utiliser [this](this.md) pour référencer des méthodes statiques ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="64478-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="64478-115">Si le mot clé `static` est appliqué à une classe, tous les membres de la classe doivent être statiques.</span><span class="sxs-lookup"><span data-stu-id="64478-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="64478-116">Les classes et les classes statiques peuvent avoir des constructeurs statiques.</span><span class="sxs-lookup"><span data-stu-id="64478-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="64478-117">Les constructeurs statiques sont appelés à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="64478-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="64478-118">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="64478-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="64478-119">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="64478-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="64478-120">Pour illustrer les membres statiques, considérons une classe qui représente un employé d’une entreprise.</span><span class="sxs-lookup"><span data-stu-id="64478-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="64478-121">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="64478-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="64478-122">La méthode et le champ n’appartiennent à aucune instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="64478-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="64478-123">Au lieu de cela, ils appartiennent à la classe entreprise.</span><span class="sxs-lookup"><span data-stu-id="64478-123">Instead they belong to the company class.</span></span> <span data-ttu-id="64478-124">Par conséquent, ils doivent être déclarés comme membres statiques de cette classe.</span><span class="sxs-lookup"><span data-stu-id="64478-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="64478-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="64478-125">Example</span></span>

<span data-ttu-id="64478-126">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="64478-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="64478-127">Pour plus de simplicité, ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="64478-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="64478-128">Dans une application réelle, ces informations doivent être lues à partir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="64478-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="64478-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="64478-129">Example</span></span>

<span data-ttu-id="64478-130">Cet exemple montre que bien que vous puissiez initialiser un champ statique à l’aide d’un autre champ statique encore non déclaré, les résultats sont indéfinis tant que vous n’assignez pas explicitement une valeur au champ statique.</span><span class="sxs-lookup"><span data-stu-id="64478-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="64478-131">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="64478-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="64478-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64478-132">See also</span></span>

- [<span data-ttu-id="64478-133">Informations de référence sur C#</span><span class="sxs-lookup"><span data-stu-id="64478-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="64478-134">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="64478-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="64478-135">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="64478-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="64478-136">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="64478-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="64478-137">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="64478-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
