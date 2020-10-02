---
description: static, modificateur - Référence C#
title: static, modificateur - Référence C#
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654637"
---
# <a name="static-c-reference"></a><span data-ttu-id="f15f3-103">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f15f3-103">static (C# Reference)</span></span>

<span data-ttu-id="f15f3-104">Cette page couvre le `static` mot clé de modificateur.</span><span class="sxs-lookup"><span data-stu-id="f15f3-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="f15f3-105">Le `static` mot clé fait également partie de la [`using static`](using-static.md) directive.</span><span class="sxs-lookup"><span data-stu-id="f15f3-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="f15f3-106">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="f15f3-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="f15f3-107">Le `static` modificateur peut être utilisé pour déclarer des `static` classes.</span><span class="sxs-lookup"><span data-stu-id="f15f3-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="f15f3-108">Dans les classes, les interfaces et les structs, vous pouvez ajouter le `static` modificateur à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="f15f3-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="f15f3-109">Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="f15f3-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="f15f3-110">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f15f3-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="f15f3-111">À compter de C# 8,0, vous pouvez ajouter le `static` modificateur à une [fonction locale](../../programming-guide/classes-and-structs/local-functions.md).</span><span class="sxs-lookup"><span data-stu-id="f15f3-111">Beginning with C# 8.0, you can add the `static` modifier to a [local function](../../programming-guide/classes-and-structs/local-functions.md).</span></span> <span data-ttu-id="f15f3-112">Une fonction locale statique ne peut pas capturer les variables locales ou l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="f15f3-112">A static local function can't capture local variables or instance state.</span></span>

<span data-ttu-id="f15f3-113">À compter de C# 9,0, vous pouvez ajouter le `static` modificateur à une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f15f3-113">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="f15f3-114">Une méthode lambda statique ou anonyme ne peut pas capturer les variables locales ou l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="f15f3-114">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="f15f3-115">Exemple : classe statique</span><span class="sxs-lookup"><span data-stu-id="f15f3-115">Example - static class</span></span>

<span data-ttu-id="f15f3-116">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="f15f3-116">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="f15f3-117">Une déclaration de constante ou de type est implicitement un `static` membre.</span><span class="sxs-lookup"><span data-stu-id="f15f3-117">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="f15f3-118">Un `static` membre ne peut pas être référencé par le biais d’une instance.</span><span class="sxs-lookup"><span data-stu-id="f15f3-118">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="f15f3-119">Au lieu de cela, elle est référencée par le nom de type.</span><span class="sxs-lookup"><span data-stu-id="f15f3-119">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="f15f3-120">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="f15f3-120">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="f15f3-121">Pour faire référence au `static` membre `x` , utilisez le nom qualifié complet, `MyBaseC.MyStruct.x` , sauf si le membre est accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="f15f3-121">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="f15f3-122">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque `static` champ.</span><span class="sxs-lookup"><span data-stu-id="f15f3-122">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="f15f3-123">Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des `static` méthodes ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="f15f3-123">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="f15f3-124">Si le `static` mot clé est appliqué à une classe, tous les membres de la classe doivent avoir la valeur `static` .</span><span class="sxs-lookup"><span data-stu-id="f15f3-124">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="f15f3-125">Les classes, les interfaces et les `static` classes peuvent avoir des `static` constructeurs.</span><span class="sxs-lookup"><span data-stu-id="f15f3-125">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="f15f3-126">Un `static` constructeur est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="f15f3-126">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="f15f3-127">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="f15f3-127">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="f15f3-128">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="f15f3-128">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="f15f3-129">Pour illustrer `static` les membres, considérez une classe qui représente un employé de la société.</span><span class="sxs-lookup"><span data-stu-id="f15f3-129">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="f15f3-130">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="f15f3-130">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="f15f3-131">La méthode et le champ n’appartiennent pas à une instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="f15f3-131">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="f15f3-132">Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="f15f3-132">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="f15f3-133">Ils doivent être déclarés en tant que `static` membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="f15f3-133">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="f15f3-134">Exemple : champ et méthode statiques</span><span class="sxs-lookup"><span data-stu-id="f15f3-134">Example - static field and method</span></span>

<span data-ttu-id="f15f3-135">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="f15f3-135">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="f15f3-136">Ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="f15f3-136">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="f15f3-137">Exemple : initialisation statique</span><span class="sxs-lookup"><span data-stu-id="f15f3-137">Example - static initialization</span></span>

<span data-ttu-id="f15f3-138">Cet exemple montre que vous pouvez initialiser un `static` champ à l’aide d’un autre `static` champ qui n’est pas encore déclaré.</span><span class="sxs-lookup"><span data-stu-id="f15f3-138">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="f15f3-139">Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au `static` champ.</span><span class="sxs-lookup"><span data-stu-id="f15f3-139">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="f15f3-140">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f15f3-140">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f15f3-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f15f3-141">See also</span></span>

- [<span data-ttu-id="f15f3-142">Référence C#</span><span class="sxs-lookup"><span data-stu-id="f15f3-142">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f15f3-143">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="f15f3-143">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f15f3-144">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="f15f3-144">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f15f3-145">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="f15f3-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f15f3-146">using static, directive</span><span class="sxs-lookup"><span data-stu-id="f15f3-146">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="f15f3-147">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="f15f3-147">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
