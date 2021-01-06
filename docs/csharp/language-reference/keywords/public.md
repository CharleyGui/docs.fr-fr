---
description: public, mot clé - Référence C#
title: public, mot clé - Référence C#
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 90c1d2a1d9efcdf57f914f4318bf7a743d3f37ec
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938466"
---
# <a name="public-c-reference"></a>public (référence C#)

Le mot clé `public` est un modificateur d’accès pour les types et les membres de types. L’accès public est le niveau d’accès le plus permissif. Il n’existe pas de restrictions d’accès aux membres publics, comme dans cet exemple :

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Pour plus d’informations, consultez [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md) et [Niveaux d’accessibilité](accessibility-levels.md).

## <a name="example"></a>Exemple

Dans l’exemple suivant, deux classes sont déclarées, `PointTest` et `Program`. L’accès aux membres publics `x` et `y` de `PointTest` s’effectue directement à partir de `Program`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Si vous remplacez le niveau d’accès `public` par [private](private.md) ou [protected](protected.md), le message d’erreur suivant s’affiche :

'PointTest.y' est inaccessible en raison de son niveau de protection.

## <a name="c-language-specification"></a>spécification du langage C#  

Pour plus d’informations, consultez [Accessibilité déclarée](~/_csharplang/spec/basic-concepts.md#declared-accessibility) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Modificateurs d’accès](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Mots clés C#](index.md)
- [Modificateurs d’accès](access-modifiers.md)
- [Niveaux d'accessibilité](accessibility-levels.md)
- [Modificateurs](index.md)
- [priv](private.md)
- [protected](protected.md)
- [intérieurs](internal.md)
