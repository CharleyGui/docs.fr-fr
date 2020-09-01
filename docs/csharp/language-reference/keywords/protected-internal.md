---
description: protected internal - Référence C#
title: protected internal - Référence C#
ms.date: 11/15/2017
f1_keywords:
- protectedinternal_CSharpKeyword
author: sputier
ms.openlocfilehash: a7537fba93c0d7145f04c6236d15c11b70f8bf98
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139435"
---
# <a name="protected-internal-c-reference"></a><span data-ttu-id="11a11-103">protected internal (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="11a11-103">protected internal (C# Reference)</span></span>

<span data-ttu-id="11a11-104">La combinaison de mots clés `protected internal` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="11a11-104">The `protected internal` keyword combination is a member access modifier.</span></span> <span data-ttu-id="11a11-105">Un membre interne protégé est accessible depuis l’assembly actif ou depuis des types dérivés de la classe conteneur.</span><span class="sxs-lookup"><span data-stu-id="11a11-105">A protected internal member is accessible from the current assembly or from types that are derived from the containing class.</span></span> <span data-ttu-id="11a11-106">Pour obtenir une comparaison de `protected internal` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="11a11-106">For a comparison of `protected internal` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="11a11-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="11a11-107">Example</span></span>

<span data-ttu-id="11a11-108">Un membre interne protégé d’une classe de base est accessible depuis n’importe quel type au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="11a11-108">A protected internal member of a base class is accessible from any type within its containing assembly.</span></span> <span data-ttu-id="11a11-109">Il est également accessible dans une classe dérivée qui se trouve dans un autre assembly seulement si l’accès s’effectue via une variable du type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="11a11-109">It is also accessible in a derived class located in another assembly only if the access occurs through a variable of the derived class type.</span></span> <span data-ttu-id="11a11-110">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="11a11-110">For example, consider the following code segment:</span></span>

```csharp
// Assembly1.cs
// Compile with: /target:library
public class BaseClass
{
   protected internal int myValue = 0;
}

class TestAccess
{
    void Access()
    {
        var baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass : BaseClass
{
    static void Main()
    {
        var baseObject = new BaseClass();
        var derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10;

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
}
```

<span data-ttu-id="11a11-111">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="11a11-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="11a11-112">Le premier fichier contient une classe de base publique, `BaseClass`, et une autre classe, `TestAccess`.</span><span class="sxs-lookup"><span data-stu-id="11a11-112">The first file contains a public base class, `BaseClass`, and another class, `TestAccess`.</span></span> <span data-ttu-id="11a11-113">`BaseClass` possède un membre interne protégé, `myValue`, à laquelle le type `TestAccess` accède.</span><span class="sxs-lookup"><span data-stu-id="11a11-113">`BaseClass` owns a protected internal member, `myValue`, which is accessed by the `TestAccess` type.</span></span>
<span data-ttu-id="11a11-114">Dans le deuxième fichier, une tentative d’accès à `myValue` via une instance de `BaseClass` génère une erreur, tandis qu’un accès à ce membre via une instance d’une classe dérivée, `DerivedClass`, réussit.</span><span class="sxs-lookup"><span data-stu-id="11a11-114">In the second file, an attempt to access `myValue` through an instance of `BaseClass` will produce an error, while an access to this member through an instance of a derived class, `DerivedClass` will succeed.</span></span>

<span data-ttu-id="11a11-115">Les membres de struct ne peuvent pas être `protected internal`, car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="11a11-115">Struct members cannot be `protected internal` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="11a11-116">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="11a11-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="11a11-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11a11-117">See also</span></span>

- [<span data-ttu-id="11a11-118">Référence C#</span><span class="sxs-lookup"><span data-stu-id="11a11-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="11a11-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="11a11-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="11a11-120">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="11a11-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="11a11-121">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="11a11-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="11a11-122">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="11a11-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="11a11-123">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="11a11-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="11a11-124">public</span><span class="sxs-lookup"><span data-stu-id="11a11-124">public</span></span>](public.md)
- [<span data-ttu-id="11a11-125">priv</span><span class="sxs-lookup"><span data-stu-id="11a11-125">private</span></span>](private.md)
- [<span data-ttu-id="11a11-126">intérieurs</span><span class="sxs-lookup"><span data-stu-id="11a11-126">internal</span></span>](internal.md)
- <span data-ttu-id="11a11-127">[Problèmes de sécurité pour les mots clés virtuels internes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11a11-127">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
