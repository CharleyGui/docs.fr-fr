---
description: using, directive - Référence C#
title: using, directive - Référence C#
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141944"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="1f9bf-103">using, directive (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1f9bf-103">using directive (C# Reference)</span></span>

<span data-ttu-id="1f9bf-104">La directive `using` a trois utilisations :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-104">The `using` directive has three uses:</span></span>

- <span data-ttu-id="1f9bf-105">Pour autoriser l'utilisation de types dans un espace de noms pour ne pas avoir à qualifier l'utilisation d'un type dans cet espace de noms :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-105">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="1f9bf-106">Pour vous permettre d’accéder aux membres statiques et aux types imbriqués d’un type sans devoir qualifier l’accès avec le nom du type.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-106">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="1f9bf-107">Pour plus d’informations, consultez la [directive using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="1f9bf-107">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="1f9bf-108">Pour créer un alias pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-108">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="1f9bf-109">Cela s’appelle une *directive using alias*.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-109">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="1f9bf-110">Le mot clé `using` est également utilisé pour créer des *instructions using<xref:System.IDisposable>, qui garantissent que les objets* tels que les fichiers et les polices sont gérés correctement.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-110">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="1f9bf-111">Pour plus d’informations, consultez [Instruction using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1f9bf-111">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="1f9bf-112">Utilisation du type statique</span><span class="sxs-lookup"><span data-stu-id="1f9bf-112">Using static type</span></span>

<span data-ttu-id="1f9bf-113">Vous pouvez accéder aux membres statiques d'un type sans devoir qualifier l'accès avec le nom du type :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-113">You can access static members of a type without having to qualify the access with the type name:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="1f9bf-114">Notes</span><span class="sxs-lookup"><span data-stu-id="1f9bf-114">Remarks</span></span>

<span data-ttu-id="1f9bf-115">La portée d'une directive `using` se limite au fichier dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-115">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="1f9bf-116">La directive `using` peut être placée :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-116">The `using` directive can appear:</span></span>

- <span data-ttu-id="1f9bf-117">Au début d’un fichier de code source, avant les définitions de type ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-117">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="1f9bf-118">Dans n’importe quel espace de noms, mais avant les espaces de noms ou types déclarés dans cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-118">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="1f9bf-119">Sinon, une erreur de compilateur [CS1529](../../misc/cs1529.md) est générée.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-119">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="1f9bf-120">Créez une directive d’alias `using` afin de faciliter la qualification d’un identificateur pour un espace de noms ou un type.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-120">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="1f9bf-121">Dans une directive `using`, le type ou l’espace de noms complet doit toujours être utilisé, indépendamment des directives `using` placées avant.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-121">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="1f9bf-122">Aucun alias `using` ne peut être utilisé dans la déclaration d’une directive `using`.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-122">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="1f9bf-123">Par exemple, les lignes ci-dessous génèrent une erreur de compilation :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-123">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="1f9bf-124">Créez une directive `using` pour utiliser les types dans un espace de noms sans avoir à spécifier l'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-124">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="1f9bf-125">Une directive `using` ne vous donne pas accès à des espaces de noms imbriqués dans l'espace de noms que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-125">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="1f9bf-126">Les espaces de noms sont organisés en deux catégories : définis par l'utilisateur et définis par le système.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-126">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="1f9bf-127">Les espaces de noms définis par l'utilisateur sont des espaces de noms définis dans votre code.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-127">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="1f9bf-128">Pour obtenir la liste des espaces de noms définis par le système, consultez [Navigateur d’API .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f9bf-128">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="1f9bf-129">Exemple 1</span><span class="sxs-lookup"><span data-stu-id="1f9bf-129">Example 1</span></span>

<span data-ttu-id="1f9bf-130">L'exemple suivant montre comment définir et utiliser un alias `using` pour un espace de noms :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="1f9bf-131">Une directive d'alias using ne peut pas avoir un type générique ouvert sur le côté droit.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="1f9bf-132">Par exemple, vous ne pouvez pas créer un alias using pour un `List<T>`, mais vous pouvez en créer un pour un `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="1f9bf-133">Exemple 2</span><span class="sxs-lookup"><span data-stu-id="1f9bf-133">Example 2</span></span>

<span data-ttu-id="1f9bf-134">L'exemple suivant montre comment définir une directive `using` et un alias `using` pour une classe :</span><span class="sxs-lookup"><span data-stu-id="1f9bf-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="1f9bf-135">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1f9bf-135">C# language specification</span></span>

<span data-ttu-id="1f9bf-136">Pour plus d’informations, consultez [Directives using](~/_csharplang/spec/namespaces.md#using-directives) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="1f9bf-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="1f9bf-137">La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="1f9bf-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f9bf-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f9bf-138">See also</span></span>

- [<span data-ttu-id="1f9bf-139">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1f9bf-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f9bf-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1f9bf-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f9bf-141">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="1f9bf-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="1f9bf-142">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1f9bf-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1f9bf-143">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="1f9bf-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="1f9bf-144">using, instruction</span><span class="sxs-lookup"><span data-stu-id="1f9bf-144">using Statement</span></span>](using-statement.md)
