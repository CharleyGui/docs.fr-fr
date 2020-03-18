---
title: Tableaux implicitement typés - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705715"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Tableaux implicitement typés (Guide de programmation C#)

Vous pouvez créer un tableau implicitement typé dans lequel le type de l’instance de tableau est déduit à partir des éléments spécifiés dans l’initialiseur de tableau. Les règles applicables à une variable implicitement typée s’appliquent aussi aux tableaux implicitement typés. Pour plus d’informations, consultez [Variables locales implicitement typées](../classes-and-structs/implicitly-typed-local-variables.md).

Les tableaux implicitement typés sont généralement utilisés dans les expressions de requête avec des types anonymes et des initialiseurs d’objets et de collections.

Les exemples suivants montrent comment créer un tableau implicitement typé :

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

Dans l’exemple précédent, vous pouvez constater que dans le cas des tableaux implicitement typés, aucun crochet n’est utilisé à gauche de l’instruction d’initialisation. Notez aussi que les tableaux en escalier sont initialisés à l’aide de `new []` à l’instar des tableaux unidimensionnels.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Tableaux implicitement typés dans les initialiseurs d’objets

Quand vous créez un type anonyme qui contient un tableau, le tableau doit être implicitement typé dans l’initialiseur d’objet du type. Dans l’exemple suivant, `contacts` est un tableau implicitement typé de types anonymes, dont chacun contient un tableau nommé `PhoneNumbers`. Notez que le mot clé `var` n’est pas utilisé dans les initialiseurs d’objets.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Variables locales implicitement dactylographiques](../classes-and-structs/implicitly-typed-local-variables.md)
- [Tableaux](./index.md)
- [Types anonymes](../classes-and-structs/anonymous-types.md)
- [Initialiseurs d’objets et de collections](../classes-and-structs/object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ en C#](../../linq/index.md)
