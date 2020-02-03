---
title: Utilisation de structs - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- structs [C#], using
ms.assetid: cea4a459-9eb9-442b-8d08-490e0797ba38
ms.openlocfilehash: 47a1da4982d22c63cb762a27313590c8ec0c5dd4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743979"
---
# <a name="using-structs-c-programming-guide"></a>Utilisation de structsC# (Guide de programmation)

Le type `struct` est approprié pour représenter des objets légers tels que `Point`, `Rectangle`et `Color`. Bien qu’il soit aussi pratique de représenter un point comme [classe](../../language-reference/keywords/class.md) avec des [propriétés implémentées automatiquement](./auto-implemented-properties.md), un [struct](../../language-reference/keywords/struct.md) peut être plus efficace dans certains scénarios. Par exemple, si vous déclarez un tableau de 1 000 objets `Point` , vous devez allouer de la mémoire supplémentaire pour faire référence à chacun des objets. Dans ce cas, un struct est moins onéreux. Étant donné que .NET contient déjà un objet appelé <xref:System.Drawing.Point>, le struct dans cet exemple est nommé `Coords` à la place.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

La définition d’un constructeur sans paramètre pour un struct constitue une erreur. Vous ne devez pas non plus initialiser un champ d'instance dans le corps d'un struct. Vous pouvez initialiser des membres de struct accessibles en externe uniquement en utilisant un constructeur paramétrable, le constructeur sans paramètre implicite ou un [initialiseur d’objet](object-and-collection-initializers.md), ou en accédant individuellement aux membres après la déclaration du struct. Tout membre privé ou inaccessible nécessite exclusivement l’utilisation de constructeurs.

Quand vous créez un objet struct avec l’opérateur [new](../../language-reference/operators/new-operator.md), cet objet est créé et le constructeur approprié est appelé conformément à la [signature du constructeur](constructors.md#constructor-syntax). Contrairement aux classes, les structs peuvent être instanciés sans avoir recours à l’opérateur `new` . Dans un tel cas, il n’y a pas d’appel au constructeur, ce qui rend l’allocation plus efficace. Toutefois, les champs ne sont pas assignés et l’objet ne peut pas être utilisé tant que tous les champs ne sont pas initialisés. Ceci inclut l’incapacité à récupérer ou à définir des valeurs au moyen de propriétés.

Si vous instanciez un objet struct à l’aide du constructeur sans paramètre, tous les membres sont assignés en fonction de leurs [valeurs par défaut](../../language-reference/builtin-types/default-values.md).

Lors de l’écriture d’un constructeur avec des paramètres pour un struct, vous devez initialiser explicitement tous les membres ; dans le cas contraire, un ou plusieurs membres ne sont pas assignés et le struct ne peut pas être utilisé, ce qui génère une erreur du compilateur [CS0171](../../misc/cs0171.md).

Il n'existe pas d'héritage pour un struct comme il en existe pour une classe. Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Toutefois, les structs héritent de la classe de base <xref:System.Object>. Un struct peut implémenter des interfaces exactement de la même manière que les classes.

Vous ne pouvez pas déclarer une classe à l’aide du mot clé `struct`. En C#, les classes et les structs ont une sémantique différente. Un struct est un type valeur, alors qu'une classe est un type référence. Pour plus d’informations, consultez [types valeur](../../language-reference/builtin-types/value-types.md) et [types référence](../../language-reference/keywords/reference-types.md).

Sauf si vous avez besoin d’une sémantique de type référence, une petite classe peut être gérée plus efficacement par le système si vous la déclarez plutôt sous forme de struct.

## <a name="example-1"></a>Exemple 1

Cet exemple illustre l’initialisation `struct` à l’aide de constructeurs sans paramètre et de constructeurs paramétrables.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#2)]

## <a name="example-2"></a>Exemple 2

Cet exemple montre une caractéristique propre aux structs. Il crée un objet Coords sans utiliser l’opérateur `new`. Si vous remplacez le mot `struct` par le mot `class`, le programme ne peut pas se compiler.

[!code-csharp[csProgGuideObjects#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#1)]

[!code-csharp[csProgGuideObjects#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#3)]

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](index.md)
- [Structures](structs.md)
