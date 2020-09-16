---
description: private protected - Référence C#
title: private protected - Référence C#
ms.date: 11/15/2017
f1_keywords:
- privateprotected_CSharpKeyword
author: sputier
ms.openlocfilehash: e7ef6d691b43abd3d07321adfc0c166629ce9098
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537299"
---
# <a name="private-protected-c-reference"></a><span data-ttu-id="9c924-103">private protected (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="9c924-103">private protected (C# Reference)</span></span>

<span data-ttu-id="9c924-104">La combinaison de mots clés `private protected` est un modificateur d’accès de membre.</span><span class="sxs-lookup"><span data-stu-id="9c924-104">The `private protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="9c924-105">Un membre protégé privé est accessible par les types dérivés de la classe conteneur, mais seulement au sein de son assembly conteneur.</span><span class="sxs-lookup"><span data-stu-id="9c924-105">A private protected member is accessible by types derived from the containing class, but only within its containing assembly.</span></span> <span data-ttu-id="9c924-106">Pour obtenir une comparaison de `private protected` et des autres modificateurs d’accès, consultez [Niveaux d’accessibilité](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9c924-106">For a comparison of `private protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9c924-107">Le modificateur d’accès `private protected` est valide dans C# 7.2 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="9c924-107">The `private protected` access modifier is valid in C# version 7.2 and later.</span></span>

## <a name="example"></a><span data-ttu-id="9c924-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9c924-108">Example</span></span>

<span data-ttu-id="9c924-109">Un membre protégé privé d’une classe de base est accessible à partir des types dérivés de son assembly conteneur seulement si le type statique de la variable est le type de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c924-109">A private protected member of a base class is accessible from derived types in its containing assembly only if the static type of the variable is the derived class type.</span></span> <span data-ttu-id="9c924-110">Prenons l’exemple de l’extrait de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9c924-110">For example, consider the following code segment:</span></span>

```csharp
public class BaseClass
{
    private protected int myValue = 0;
}

public class DerivedClass1 : BaseClass
{
    void Access()
    {
        var baseObject = new BaseClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 5;

        // OK, accessed through the current derived class instance
        myValue = 5;
    }
}
```

```csharp
// Assembly2.cs
// Compile with: /reference:Assembly1.dll
class DerivedClass2 : BaseClass
{
    void Access()
    {
        // Error CS0122, because myValue can only be
        // accessed by types in Assembly1
        // myValue = 10;
    }
}
```

<span data-ttu-id="9c924-111">Cet exemple contient deux fichiers : `Assembly1.cs` et `Assembly2.cs`.</span><span class="sxs-lookup"><span data-stu-id="9c924-111">This example contains two files, `Assembly1.cs` and `Assembly2.cs`.</span></span>
<span data-ttu-id="9c924-112">Le premier fichier contient une classe de base publique, `BaseClass`, et un type qui en est dérivé, `DerivedClass1`.</span><span class="sxs-lookup"><span data-stu-id="9c924-112">The first file contains a public base class, `BaseClass`, and a type derived from it, `DerivedClass1`.</span></span> <span data-ttu-id="9c924-113">`BaseClass` possède un membre protégé privé, `myValue`, auquel `DerivedClass1` tente d’accéder de deux manières.</span><span class="sxs-lookup"><span data-stu-id="9c924-113">`BaseClass` owns a private protected member, `myValue`, which `DerivedClass1` tries to access in two ways.</span></span> <span data-ttu-id="9c924-114">La première tentative d’accès à `myValue` via une instance de `BaseClass` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="9c924-114">The first attempt to access `myValue` through an instance of `BaseClass` will produce an error.</span></span> <span data-ttu-id="9c924-115">Cependant, la tentative de l’utiliser comme un membre hérité dans `DerivedClass1` réussit.</span><span class="sxs-lookup"><span data-stu-id="9c924-115">However, the attempt to use it as an inherited member in `DerivedClass1` will succeed.</span></span>

<span data-ttu-id="9c924-116">Dans le deuxième fichier, une tentative d’accès à `myValue` en tant que membre hérité de `DerivedClass2` génère une erreur, car il est accessible seulement par des types dérivés dans Assembly1.</span><span class="sxs-lookup"><span data-stu-id="9c924-116">In the second file, an attempt to access `myValue` as an inherited member of `DerivedClass2` will produce an error, as it is only accessible by derived types in Assembly1.</span></span>

<span data-ttu-id="9c924-117">Si `Assembly1.cs` contient un <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> nom `Assembly2` , la classe dérivée aura `DerivedClass1` accès aux `private protected` membres déclarés dans `BaseClass` .</span><span class="sxs-lookup"><span data-stu-id="9c924-117">If `Assembly1.cs` contains an <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> that names `Assembly2`, the derived class `DerivedClass1` will have access to `private protected` members declared in `BaseClass`.</span></span> <span data-ttu-id="9c924-118">`InternalsVisibleTo` rend `private protected` les membres visibles aux classes dérivées dans d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="9c924-118">`InternalsVisibleTo` makes `private protected` members visible to derived classes in other assemblies.</span></span>

<span data-ttu-id="9c924-119">Les membres de struct ne peuvent pas être `private protected`, car le struct ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="9c924-119">Struct members cannot be `private protected` because the struct cannot be inherited.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9c924-120">spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9c924-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9c924-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c924-121">See also</span></span>

- [<span data-ttu-id="9c924-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="9c924-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9c924-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9c924-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9c924-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="9c924-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9c924-125">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="9c924-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="9c924-126">Niveaux d'accessibilité</span><span class="sxs-lookup"><span data-stu-id="9c924-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="9c924-127">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="9c924-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9c924-128">public</span><span class="sxs-lookup"><span data-stu-id="9c924-128">public</span></span>](public.md)
- [<span data-ttu-id="9c924-129">private</span><span class="sxs-lookup"><span data-stu-id="9c924-129">private</span></span>](private.md)
- [<span data-ttu-id="9c924-130">intérieurs</span><span class="sxs-lookup"><span data-stu-id="9c924-130">internal</span></span>](internal.md)
- <span data-ttu-id="9c924-131">[Problèmes de sécurité pour les mots clés virtuels internes](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9c924-131">[Security concerns for internal virtual keywords](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
