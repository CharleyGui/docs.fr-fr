---
title: using, directive - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970057"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="cc222-102">using, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="cc222-102">using directive (C# Reference)</span></span>

<span data-ttu-id="cc222-103">La directive `using` a trois utilisations :</span><span class="sxs-lookup"><span data-stu-id="cc222-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="cc222-104">Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :</span><span class="sxs-lookup"><span data-stu-id="cc222-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="cc222-105">Pour vous permettre d’accéder aux membres statiques et aux types imbriqués d’un type sans devoir qualifier l’accès avec le nom du type.</span><span class="sxs-lookup"><span data-stu-id="cc222-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="cc222-106">Pour plus d’informations, consultez la [directive using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="cc222-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="cc222-107">Pour créer un alias pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="cc222-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="cc222-108">Cela s’appelle une *directive using alias*.</span><span class="sxs-lookup"><span data-stu-id="cc222-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="cc222-109">Le mot clé `using` est également utilisé pour créer des *instructions using<xref:System.IDisposable>, qui garantissent que les objets*  tels que les fichiers et les polices sont gérés correctement.</span><span class="sxs-lookup"><span data-stu-id="cc222-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="cc222-110">Pour plus d’informations, consultez [Instruction using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cc222-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="cc222-111">Utilisation du type statique</span><span class="sxs-lookup"><span data-stu-id="cc222-111">Using static type</span></span>

<span data-ttu-id="cc222-112">Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :</span><span class="sxs-lookup"><span data-stu-id="cc222-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="cc222-113">Notes</span><span class="sxs-lookup"><span data-stu-id="cc222-113">Remarks</span></span>

<span data-ttu-id="cc222-114">La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="cc222-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="cc222-115">La directive `using` peut être placée :</span><span class="sxs-lookup"><span data-stu-id="cc222-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="cc222-116">Au début d’un fichier de code source, avant les définitions de type ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc222-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="cc222-117">Dans n’importe quel espace de noms, mais avant les espaces de noms ou types déclarés dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc222-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="cc222-118">Sinon, une erreur de compilateur [CS1529](../../misc/cs1529.md) est générée.</span><span class="sxs-lookup"><span data-stu-id="cc222-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="cc222-119">Créez une directive d’alias `using` afin de faciliter la qualification d’un identificateur pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="cc222-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="cc222-120">Dans une directive `using`, le type ou l’espace de noms complet doit toujours être utilisé, indépendamment des directives `using` placées avant.</span><span class="sxs-lookup"><span data-stu-id="cc222-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="cc222-121">Aucun alias `using` ne peut être utilisé dans la déclaration d’une directive `using`.</span><span class="sxs-lookup"><span data-stu-id="cc222-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="cc222-122">Par exemple, les lignes ci-dessous génèrent une erreur de compilation :</span><span class="sxs-lookup"><span data-stu-id="cc222-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="cc222-123">Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc222-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="cc222-124">Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="cc222-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="cc222-125">Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système.</span><span class="sxs-lookup"><span data-stu-id="cc222-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="cc222-126">Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code.</span><span class="sxs-lookup"><span data-stu-id="cc222-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="cc222-127">Pour obtenir la liste des espaces de noms définis par le système, consultez [Navigateur d’API .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc222-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="cc222-128">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="cc222-128">Example 1</span></span>

<span data-ttu-id="cc222-129">L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="cc222-129">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="cc222-130">Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit.</span><span class="sxs-lookup"><span data-stu-id="cc222-130">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="cc222-131">Par exemple, vous ne pouvez pas créer un alias using pour un `List<T>`, mais vous pouvez en créer un pour un `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="cc222-131">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="cc222-132">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="cc222-132">Example 2</span></span>

<span data-ttu-id="cc222-133">L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :</span><span class="sxs-lookup"><span data-stu-id="cc222-133">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="cc222-134">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="cc222-134">C# language specification</span></span>

<span data-ttu-id="cc222-135">Pour plus d’informations, consultez [Directives using](~/_csharplang/spec/namespaces.md#using-directives) dans la [spécification du langage C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc222-135">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="cc222-136">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="cc222-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc222-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc222-137">See also</span></span>

- [<span data-ttu-id="cc222-138">Référence C#</span><span class="sxs-lookup"><span data-stu-id="cc222-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc222-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="cc222-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc222-140">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="cc222-140">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="cc222-141">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="cc222-141">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cc222-142">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="cc222-142">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="cc222-143">using, instruction</span><span class="sxs-lookup"><span data-stu-id="cc222-143">using Statement</span></span>](using-statement.md)
