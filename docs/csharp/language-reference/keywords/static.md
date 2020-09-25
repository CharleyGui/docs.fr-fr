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
ms.openlocfilehash: ccd575748c2286fa7348e2880acbfadd036d9ccd
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247720"
---
# <a name="static-c-reference"></a><span data-ttu-id="40457-103">static (référence C#)</span><span class="sxs-lookup"><span data-stu-id="40457-103">static (C# Reference)</span></span>

<span data-ttu-id="40457-104">Cette page couvre le `static` mot clé de modificateur.</span><span class="sxs-lookup"><span data-stu-id="40457-104">This page covers the `static` modifier keyword.</span></span> <span data-ttu-id="40457-105">Le `static` mot clé fait également partie de la [`using static`](using-static.md) directive.</span><span class="sxs-lookup"><span data-stu-id="40457-105">The `static` keyword is also part of the [`using static`](using-static.md) directive.</span></span>

<span data-ttu-id="40457-106">Utilisez le modificateur `static` pour déclarer un membre statique, qui appartient au type lui-même plutôt qu’à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="40457-106">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="40457-107">Le `static` modificateur peut être utilisé pour déclarer des `static` classes.</span><span class="sxs-lookup"><span data-stu-id="40457-107">The `static` modifier can be used to declare `static` classes.</span></span> <span data-ttu-id="40457-108">Dans les classes, les interfaces et les structs, vous pouvez ajouter le `static` modificateur à des champs, des méthodes, des propriétés, des opérateurs, des événements et des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="40457-108">In classes, interfaces, and structs, you may add the `static` modifier to fields, methods, properties, operators, events, and constructors.</span></span> <span data-ttu-id="40457-109">Le `static` modificateur ne peut pas être utilisé avec des indexeurs ou des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="40457-109">The `static` modifier can't be used with indexers or finalizers.</span></span> <span data-ttu-id="40457-110">Pour plus d’informations, consultez la page [Classes statiques et membres de classes statiques](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="40457-110">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="40457-111">À compter de C# 9,0, vous pouvez ajouter le `static` modificateur à une [expression lambda](../operators/lambda-expressions.md) ou une [méthode anonyme](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="40457-111">Beginning with C# 9.0, you can add the `static` modifier to a [lambda expression](../operators/lambda-expressions.md) or [anonymous method](../operators/delegate-operator.md).</span></span> <span data-ttu-id="40457-112">Une méthode lambda statique ou anonyme ne peut pas capturer les variables locales ou l’état de l’instance.</span><span class="sxs-lookup"><span data-stu-id="40457-112">A static lambda or anonymous method can't capture local variables or instance state.</span></span>

## <a name="example---static-class"></a><span data-ttu-id="40457-113">Exemple : classe statique</span><span class="sxs-lookup"><span data-stu-id="40457-113">Example - static class</span></span>

<span data-ttu-id="40457-114">La classe suivante est déclarée comme `static` et contient uniquement des méthodes `static` :</span><span class="sxs-lookup"><span data-stu-id="40457-114">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="40457-115">Une déclaration de constante ou de type est implicitement un `static` membre.</span><span class="sxs-lookup"><span data-stu-id="40457-115">A constant or type declaration is implicitly a `static` member.</span></span> <span data-ttu-id="40457-116">Un `static` membre ne peut pas être référencé par le biais d’une instance.</span><span class="sxs-lookup"><span data-stu-id="40457-116">A `static` member can't be referenced through an instance.</span></span> <span data-ttu-id="40457-117">Au lieu de cela, elle est référencée par le nom de type.</span><span class="sxs-lookup"><span data-stu-id="40457-117">Instead, it's referenced through the type name.</span></span> <span data-ttu-id="40457-118">Par exemple, considérons la classe suivante :</span><span class="sxs-lookup"><span data-stu-id="40457-118">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="40457-119">Pour faire référence au `static` membre `x` , utilisez le nom qualifié complet, `MyBaseC.MyStruct.x` , sauf si le membre est accessible à partir de la même portée :</span><span class="sxs-lookup"><span data-stu-id="40457-119">To refer to the `static` member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="40457-120">Alors qu’une instance d’une classe contient une copie distincte de tous les champs d’instance de la classe, il n’existe qu’une seule copie de chaque `static` champ.</span><span class="sxs-lookup"><span data-stu-id="40457-120">While an instance of a class contains a separate copy of all instance fields of the class, there's only one copy of each `static` field.</span></span>

<span data-ttu-id="40457-121">Il n’est pas possible d’utiliser [`this`](this.md) pour référencer des `static` méthodes ou des accesseurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="40457-121">It isn't possible to use [`this`](this.md) to reference `static` methods or property accessors.</span></span>

<span data-ttu-id="40457-122">Si le `static` mot clé est appliqué à une classe, tous les membres de la classe doivent avoir la valeur `static` .</span><span class="sxs-lookup"><span data-stu-id="40457-122">If the `static` keyword is applied to a class, all the members of the class must be `static`.</span></span>

<span data-ttu-id="40457-123">Les classes, les interfaces et les `static` classes peuvent avoir des `static` constructeurs.</span><span class="sxs-lookup"><span data-stu-id="40457-123">Classes, interfaces, and `static` classes may have `static` constructors.</span></span> <span data-ttu-id="40457-124">Un `static` constructeur est appelé à un moment donné entre le démarrage du programme et l’instanciation de la classe.</span><span class="sxs-lookup"><span data-stu-id="40457-124">A `static` constructor is called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="40457-125">L’utilisation du mot clé `static` est plus restreinte que dans C++.</span><span class="sxs-lookup"><span data-stu-id="40457-125">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="40457-126">Pour comparer avec le mot clé C++, consultez [Classes de stockage (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="40457-126">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="40457-127">Pour illustrer `static` les membres, considérez une classe qui représente un employé de la société.</span><span class="sxs-lookup"><span data-stu-id="40457-127">To demonstrate `static` members, consider a class that represents a company employee.</span></span> <span data-ttu-id="40457-128">Supposons que la classe contient une méthode pour compter les employés et un champ pour stocker le nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="40457-128">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="40457-129">La méthode et le champ n’appartiennent pas à une instance d’employé.</span><span class="sxs-lookup"><span data-stu-id="40457-129">Both the method and the field don't belong to any one employee instance.</span></span> <span data-ttu-id="40457-130">Au lieu de cela, ils appartiennent à la classe des employés dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="40457-130">Instead, they belong to the class of employees as a whole.</span></span> <span data-ttu-id="40457-131">Ils doivent être déclarés en tant que `static` membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="40457-131">They should be declared as `static` members of the class.</span></span>

## <a name="example---static-field-and-method"></a><span data-ttu-id="40457-132">Exemple : champ et méthode statiques</span><span class="sxs-lookup"><span data-stu-id="40457-132">Example - static field and method</span></span>

<span data-ttu-id="40457-133">Cet exemple lit le nom et l’ID d’un nouvel employé, incrémente d’une unité le compteur d’employés et affiche les informations concernant le nouvel employé et le nouveau nombre d’employés.</span><span class="sxs-lookup"><span data-stu-id="40457-133">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="40457-134">Ce programme lit le nombre actuel d’employés à partir du clavier.</span><span class="sxs-lookup"><span data-stu-id="40457-134">This program reads the current number of employees from the keyboard.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a><span data-ttu-id="40457-135">Exemple : initialisation statique</span><span class="sxs-lookup"><span data-stu-id="40457-135">Example - static initialization</span></span>

<span data-ttu-id="40457-136">Cet exemple montre que vous pouvez initialiser un `static` champ à l’aide d’un autre `static` champ qui n’est pas encore déclaré.</span><span class="sxs-lookup"><span data-stu-id="40457-136">This example shows that you can initialize a `static` field by using another `static` field that is not yet declared.</span></span> <span data-ttu-id="40457-137">Les résultats ne sont pas définis tant que vous n’affectez pas explicitement une valeur au `static` champ.</span><span class="sxs-lookup"><span data-stu-id="40457-137">The results will be undefined until you explicitly assign a value to the `static` field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="40457-138">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="40457-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="40457-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40457-139">See also</span></span>

- [<span data-ttu-id="40457-140">Référence C#</span><span class="sxs-lookup"><span data-stu-id="40457-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40457-141">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="40457-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40457-142">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="40457-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="40457-143">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="40457-143">Modifiers</span></span>](index.md)
- [<span data-ttu-id="40457-144">using static, directive</span><span class="sxs-lookup"><span data-stu-id="40457-144">using static directive</span></span>](using-static.md)
- [<span data-ttu-id="40457-145">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="40457-145">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
