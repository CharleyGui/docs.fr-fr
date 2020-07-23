---
title: Guide pratique pour créer une Union C/C++ à l’aide d’attributs (C#)
description: Découvrez comment utiliser des attributs pour personnaliser la façon dont les structs sont disposés en mémoire en C#. Cet exemple implémente l’équivalent d’une Union à partir de C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925070"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="b6821-104">Guide pratique pour créer une Union C/C++ à l’aide d’attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="b6821-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="b6821-105">À l’aide d’attributs, vous pouvez personnaliser la disposition des structs en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b6821-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="b6821-106">Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide des attributs `StructLayout(LayoutKind.Explicit)` et `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="b6821-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="b6821-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6821-107">Example</span></span>

<span data-ttu-id="b6821-108">Dans ce segment de code, tous les champs de `TestUnion` débutent au même emplacement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="b6821-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="b6821-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6821-109">Example</span></span>

<span data-ttu-id="b6821-110">Voici un autre exemple où les champs débutent à différents emplacements définis explicitement.</span><span class="sxs-lookup"><span data-stu-id="b6821-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="b6821-111">Les deux champs entiers, `i1` et `i2`, partagent leurs emplacements de mémoire avec `lg`.</span><span class="sxs-lookup"><span data-stu-id="b6821-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="b6821-112">Ce type de contrôle sur la disposition des structs est utile quand vous utilisez des appels de code non managé.</span><span class="sxs-lookup"><span data-stu-id="b6821-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6821-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6821-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="b6821-114">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="b6821-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="b6821-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6821-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="b6821-116">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="b6821-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="b6821-117">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="b6821-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="b6821-118">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="b6821-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="b6821-119">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="b6821-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
