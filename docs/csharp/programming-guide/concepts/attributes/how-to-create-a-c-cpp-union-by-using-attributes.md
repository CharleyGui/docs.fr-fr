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
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Guide pratique pour créer une Union C/C++ à l’aide d’attributs (C#)

À l’aide d’attributs, vous pouvez personnaliser la disposition des structs en mémoire. Par exemple, vous pouvez créer ce qu’on appelle une union en C/C++ à l’aide des attributs `StructLayout(LayoutKind.Explicit)` et `FieldOffset`.

## <a name="example"></a>Exemple

Dans ce segment de code, tous les champs de `TestUnion` débutent au même emplacement en mémoire.

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

## <a name="example"></a>Exemple

Voici un autre exemple où les champs débutent à différents emplacements définis explicitement.

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

Les deux champs entiers, `i1` et `i2`, partagent leurs emplacements de mémoire avec `lg`. Ce type de contrôle sur la disposition des structs est utile quand vous utilisez des appels de code non managé.

## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Guide de programmation C#](../../index.md)
- [Attributs](../../../../standard/attributes/index.md)
- [Réflexion (C#)](../reflection.md)
- [Attributs (C#)](index.md)
- [Création d’attributs personnalisés (C#)](creating-custom-attributes.md)
- [Accès à des attributs à l’aide de la réflexion (C#)](accessing-attributes-by-using-reflection.md)
