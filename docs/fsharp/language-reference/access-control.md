---
title: Contrôle d’accès
description: Découvrez comment contrôler l’accès aux éléments de programmation, tels que les types, les méthodes et les fonctions F# , dans le langage de programmation.
ms.date: 05/16/2016
ms.openlocfilehash: ed77a09cf87aabf9a4134276e89e84aa42abd3c3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629962"
---
# <a name="access-control"></a>Contrôle d’accès

*Le contrôle d’accès* fait référence à la déclaration des clients qui peuvent utiliser certains éléments de programme, tels que des types, des méthodes et des fonctions.

## <a name="basics-of-access-control"></a>Notions de base de Access Control

Dans F#, les spécificateurs `public`de contrôle d' `internal`accès, `private` et peuvent être appliqués à des modules, des types, des méthodes, des définitions de valeur, des fonctions, des propriétés et des champs explicites.

- `public`indique que l’entité est accessible par tous les appelants.

- `internal`indique que l’entité est accessible uniquement à partir du même assembly.

- `private`indique que l’entité est accessible uniquement à partir du type englobant ou du module.

> [!NOTE]
> Le spécificateur `protected` d’accès n’est pas utilisé F#dans, bien qu’il soit acceptable si vous utilisez des types créés dans des langages `protected` qui prennent en charge l’accès. Par conséquent, si vous substituez une méthode protégée, votre méthode reste accessible uniquement dans la classe et ses descendants.

En général, le spécificateur est placé devant le nom de l’entité, sauf quand un spécificateur ou `mutable` `inline` est utilisé, qui apparaît après le spécificateur de contrôle d’accès.

Si aucun spécificateur d’accès n’est utilisé, la valeur `public`par défaut est `let` , à l’exception des liaisons dans un type `private` , qui sont toujours au type.

Les signatures F# dans fournissent un autre mécanisme de contrôle F# de l’accès aux éléments de programme. Les signatures ne sont pas requises pour le contrôle d’accès. Pour plus d’informations, consultez [Signatures](signatures.md).

## <a name="rules-for-access-control"></a>Règles pour Access Control

Le contrôle d’accès est soumis aux règles suivantes:

- Les déclarations d’héritage (autrement dit, l' `inherit` utilisation de pour spécifier une classe de base pour une classe), les déclarations d’interface (c’est-à-dire la spécification d’une classe qui implémente une interface) et les membres abstraits ont toujours la même accessibilité que le type englobant. Par conséquent, un spécificateur de contrôle d’accès ne peut pas être utilisé sur ces constructions.

- L’accessibilité des cas individuels dans une union discriminée est déterminée par l’accessibilité de l’union discriminée elle-même. Autrement dit, un cas d’Union particulier n’est pas moins accessible que l’Union elle-même.

- L’accessibilité des champs individuels d’un type d’enregistrement ne peut pas être déterminée par l’accessibilité de l’enregistrement lui-même. Autrement dit, une étiquette d’enregistrement particulière n’est pas moins accessible que l’enregistrement lui-même.

## <a name="example"></a>Exemples

Le code suivant illustre l’utilisation de spécificateurs de contrôle d’accès. Il y a deux fichiers dans le projet `Module1.fs` , `Module2.fs`et. Chaque fichier est implicitement un module. Par conséquent, il existe deux modules `Module1` , `Module2`et. Un type privé et un type interne sont définis dans `Module1`. Le type privé n’est pas accessible `Module2`à partir de, mais le type interne peut.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet1.fs)]

Le code suivant teste l’accessibilité des types créés dans `Module1.fs`.

[!code-fsharp[Main](~/samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Signatures](signatures.md)
