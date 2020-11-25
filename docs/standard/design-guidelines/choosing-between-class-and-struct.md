---
title: Choix entre classe et structure
description: Apprenez à décider s’il est possible de concevoir un type en tant que classe ou de concevoir un type en tant que struct. Comprendre comment les types référence et les types valeur diffèrent dans .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
ms.openlocfilehash: 05ba9abbc9495d927b7f58ebb06f152c0c15772f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701248"
---
# <a name="choosing-between-class-and-struct"></a>Choix entre classe et structure

L’une des décisions de conception de base de chaque concepteur d’infrastructure est de concevoir un type en tant que classe (type référence) ou en tant que struct (un type valeur). Il est essentiel de bien comprendre les différences de comportement des types de référence et des types de valeur pour faire ce choix.

 La première différence entre les types référence et les types valeur est que nous envisageons que les types référence sont alloués sur le tas et récupérés par le garbage collector, tandis que les types valeur sont alloués sur la pile ou inline dans les types contenants et désalloués lorsque la pile se déroule ou lorsque leur type conteneur est libéré. Par conséquent, les allocations et les désallocations de types valeur sont en général moins coûteuses que les allocations et les désallocations de types référence.

 Ensuite, les tableaux de types référence sont alloués hors ligne, ce qui signifie que les éléments de tableau sont simplement des références aux instances du type référence résidant sur le tas. Les tableaux de types valeur sont alloués inline, ce qui signifie que les éléments de tableau sont les instances réelles du type valeur. Par conséquent, les allocations et les désallocations des tableaux de types valeur sont très coûteuses que les allocations et les désallocations de tableaux de types référence. En outre, dans la majorité des cas, les tableaux de types valeur présentent une plus grande localité de référence.

 La différence suivante est liée à l’utilisation de la mémoire. Les types valeur sont boxed lorsqu’ils sont castés en un type référence ou l’une des interfaces qu’ils implémentent. Ils obtiennent unboxed lorsqu’ils sont reconvertis en type valeur. Étant donné que les zones sont des objets alloués sur le tas et qui sont récupérés par le garbage collector, un trop grand nombre de conversions boxing et unboxing peuvent avoir un impact négatif sur le tas, le garbage collector et enfin sur les performances de l’application.  En revanche, aucune conversion boxing de ce type ne se produit, car les types référence sont convertis. (Pour plus d’informations, consultez [conversion boxing et unboxing](../../csharp/programming-guide/types/boxing-and-unboxing.md)).

 Ensuite, les assignations de type référence copient la référence, tandis que les assignations de type valeur copient la valeur entière. Par conséquent, les assignations de types de référence volumineux sont moins coûteuses que les assignations de types de valeur élevée.

 Enfin, les types référence sont passés par référence, tandis que les types valeur sont passés par valeur. Les modifications apportées à une instance d’un type référence affectent toutes les références pointant vers l’instance. Les instances de type valeur sont copiées lorsqu’elles sont passées par valeur. Quand une instance d’un type valeur est modifiée, elle n’affecte pas l’une de ses copies. Étant donné que les copies ne sont pas créées explicitement par l’utilisateur mais sont implicitement créées lorsque des arguments sont passés ou que des valeurs de retour sont retournées, les types valeur qui peuvent être modifiés peuvent être déroutants pour de nombreux utilisateurs. Par conséquent, les types valeur doivent être immuables.

 En règle générale, la majorité des types dans un Framework doivent être des classes. Toutefois, il existe certaines situations dans lesquelles les caractéristiques d’un type de valeur rendent l’utilisation de structs plus appropriée.

 ✔️ ENVISAGER de définir un struct au lieu d’une classe si les instances du type sont petites et généralement éphémères ou sont généralement incorporées dans d’autres objets.

 ❌ Évitez de définir un struct à moins que le type ait toutes les caractéristiques suivantes :

- Il représente logiquement une valeur unique, similaire aux types primitifs ( `int` , `double` , etc.).

- Elle a une taille d’instance inférieure à 16 octets.

- Elle est immuable.

- Il n’est pas nécessaire d’effectuer fréquemment des Boxing.

 Dans tous les autres cas, vous devez définir vos types en tant que classes.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de type](type.md)
- [Directives de conception d’infrastructure](index.md)
