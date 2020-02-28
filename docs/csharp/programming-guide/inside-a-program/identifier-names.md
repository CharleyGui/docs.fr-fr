---
title: Noms d’identificateurs
description: Découvrez les règles relatives aux noms d’identificateurs valides dans le langage de programmation C#.
ms.date: 08/21/2018
ms.openlocfilehash: bef6e2ea285b5391af3350ae42a4105d140c6d1b
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673366"
---
# <a name="identifier-names"></a>Noms d’identificateurs

Un **identificateur** est le nom que vous assignez à un type (classe, interface, struct, délégué ou enum), un membre, une variable ou un espace de noms. Les identificateurs valides doivent suivre les règles suivantes :

- Les identificateurs doivent commencer par une lettre ou par `_`.
- Les identificateurs peuvent contenir des lettres Unicode, des nombres décimaux, des caractères de connexion Unicode, des caractères de combinaison Unicode ou des caractères de mise en forme Unicode. Pour plus d’informations sur les catégories Unicode, consultez la [Base de données des catégories Unicode](https://www.unicode.org/reports/tr44/).
Vous pouvez déclarer des identificateurs qui correspondent à des mots clés C# en utilisant le préfixe `@` sur l’identificateur. `@` ne fait pas partie du nom de l’identificateur. Par exemple, `@if` déclare un identificateur nommé `if`. Ces [identificateurs textuels](../../language-reference/tokens/verbatim.md) sont destinés principalement à assurer l’interopérabilité avec les identificateurs déclarés dans d’autres langages.

Pour une définition complète des identificateurs valides, consultez la rubrique [Identificateurs dans la spécification du langage C#](../../../../_csharplang/spec/lexical-structure.md#identifiers).

## <a name="naming-conventions"></a>Conventions d’affectation de noms

En plus des règles, un certain nombre de [conventions de nommage](../../../standard/design-guidelines/naming-guidelines.md) des identificateurs sont utilisées dans les API .NET. Par convention, les programmes C# utilisent `PascalCase` pour les noms de types, les espaces de noms et tous les membres publics. De plus, les conventions suivantes sont communément respectées :

- Les noms d’interfaces commencent par un `I` majuscule.
- Les types d’attribut finissent par le mot `Attribute`.
- Les types enum utilisent un nom singulier pour les non-indicateurs et un nom pluriel pour les indicateurs.
- Les identificateurs ne doivent pas contenir deux caractères `_` consécutifs. Ces noms sont réservés aux identificateurs générés par le compilateur.

## <a name="c-language-specification"></a>Spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [À l’intérieur d’un programme C#](./index.md)
- [Informations de référence sur C#](../../language-reference/index.md)
- [Classes](../classes-and-structs/classes.md)
- [Types de structures](../../language-reference/builtin-types/struct.md)
- [Espaces de noms](../namespaces/index.md)
- [Interfaces](../interfaces/index.md)
- [Délégués](../delegates/index.md)
