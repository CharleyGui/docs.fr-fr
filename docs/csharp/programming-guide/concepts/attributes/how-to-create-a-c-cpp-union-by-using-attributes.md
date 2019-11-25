---
title: Comment créer un C/C++ Union à l’aide d’attributsC#()
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141574"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="9e817-102">Comment créer un C/C++ Union à l’aide d’attributsC#()</span><span class="sxs-lookup"><span data-stu-id="9e817-102">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="9e817-103">À l’aide d’attributs, vous pouvez personnaliser la disposition des structs en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9e817-103">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="9e817-104">Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide des attributs `StructLayout(LayoutKind.Explicit)` et `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="9e817-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="9e817-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e817-105">Example</span></span>

<span data-ttu-id="9e817-106">Dans ce segment de code, tous les champs de `TestUnion` débutent au même emplacement en mémoire.</span><span class="sxs-lookup"><span data-stu-id="9e817-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="9e817-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e817-107">Example</span></span>

<span data-ttu-id="9e817-108">Voici un autre exemple où les champs débutent à différents emplacements définis explicitement.</span><span class="sxs-lookup"><span data-stu-id="9e817-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="9e817-109">Les deux champs entiers, `i1` et `i2`, partagent leurs emplacements de mémoire avec `lg`.</span><span class="sxs-lookup"><span data-stu-id="9e817-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="9e817-110">Ce type de contrôle sur la disposition des structs est utile quand vous utilisez des appels de code non managé.</span><span class="sxs-lookup"><span data-stu-id="9e817-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e817-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e817-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="9e817-112">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="9e817-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="9e817-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="9e817-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="9e817-114">Réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="9e817-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="9e817-115">Attributs (C#)</span><span class="sxs-lookup"><span data-stu-id="9e817-115">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="9e817-116">Création d’attributs personnalisés (C#)</span><span class="sxs-lookup"><span data-stu-id="9e817-116">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="9e817-117">Accès à des attributs à l’aide de la réflexion (C#)</span><span class="sxs-lookup"><span data-stu-id="9e817-117">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
