---
title: Compatibilité
description: En savoir plus sur la façon dont les modifications du code peuvent affecter la compatibilité dans .NET.
ms.date: 06/10/2019
ms.openlocfilehash: 1cf14b7ff4143367653bd1c305cc1dda6711f980
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415691"
---
# <a name="how-code-changes-can-affect-compatibility"></a>Comment les modifications du code peuvent affecter la compatibilité

*Compatibilité* fait référence à la possibilité de compiler ou d’exécuter du code sur une version d’une implémentation de .NET autre que celle avec laquelle le code a été développé à l’origine. Une [modification particulière](index.md) peut affecter la compatibilité de six façons différentes :

- [Changements de comportement](#behavioral-change)
- [Compatibilité binaire](#binary-compatibility)
- [Compatibilité source](#source-compatibility)
- [Compatibilité au moment du design](#design-time-compatibility)
- [Compatibilité descendante](#backwards-compatibility)
- [Compatibilité ascendante](#forward-compatibility) (pas un objectif de .net Core)

## <a name="behavioral-change"></a>Changements de comportement

Un changement de comportement représente un changement du comportement d’un membre. Le changement peut être visible de l’extérieur (par exemple, une méthode peut lever une autre exception) ou il peut représenter une implémentation modifiée (par exemple, une modification de la façon dont une valeur de retour est calculée, l’ajout ou la suppression d’appels de méthode internes, ou même une amélioration significative des performances).

Quand des changements de comportement sont visibles de l’extérieur et modifient le contrat public d’un type, ils sont faciles à évaluer, car ils affectent la compatibilité binaire. Les changements d’implémentation sont bien plus difficiles à évaluer : en fonction de la nature du changement et de la fréquence et des modèles d’utilisation de l’API, l’impact d’un changement peut aller de grave à banal.

## <a name="binary-compatibility"></a>Compatibilité binaire

La compatibilité binaire fait référence à la capacité d’un consommateur d’une API à utiliser l’API sur une version plus récente sans recompilation. De tels changements, comme l’ajout de méthodes ou l’ajout d’une nouvelle implémentation d’une interface avec un type, n’affectent pas la compatibilité binaire. Cependant, la suppression ou la modification des signatures publiques d’un assembly, dont le résultat est que les consommateurs ne peuvent plus accéder à la même interface exposée par l’assembly, affectent la compatibilité binaire. Un changement de ce type est appelé *changement non compatible au niveau binaire*.

## <a name="source-compatibility"></a>Compatibilité source

La compatibilité source fait référence à la capacité des consommateurs existants d’une API à effectuer une recompilation avec une version plus récente sans aucune modification de la source. Un *changement incompatible au niveau source* se produit quand un consommateur doit modifier le code source pour qu’il soit généré avec succès sur une version plus récente d’une API.

## <a name="design-time-compatibility"></a>Compatibilité au moment du design

La compatibilité au moment du design fait référence à la préservation de l’expérience au moment du design entre les versions de Visual Studio et d’autres environnements utilisés au moment du design. Bien que cela puisse impliquer le comportement ou l’interface utilisateur des concepteurs, l’aspect le plus important de la compatibilité au moment du design concerne la compatibilité des projets. Un projet ou une solution doit pouvoir être ouvert et utilisé sur une version plus récente de l’environnement utilisé au moment du design.

## <a name="backwards-compatibility"></a>Compatibilité descendante

La compatibilité descendante fait référence à la capacité d’un consommateur existant d’une API à s’exécuter avec une nouvelle version tout en se comportant de la même façon. Les changements de comportement et les changements de compatibilité binaire affectent la compatibilité descendante. Si un consommateur ne peut pas s’exécuter ou se comporte différemment lors de l’exécution avec une version plus récente de l’API, l’API est *incompatible au niveau descendant*.

Les modifications qui affectent la compatibilité descendante sont déconseillées, car les développeurs s’attendent à une compatibilité descendante dans les versions plus récentes d’une API.

## <a name="forward-compatibility"></a>Compatibilité ascendante

La compatibilité ascendante fait référence à la capacité d’un consommateur existant d’une API à s’exécuter avec une version plus ancienne tout en montrant le même comportement. Si un consommateur ne peut pas s’exécuter ou se comporte différemment lors de l’exécution avec une version plus ancienne de l’API, l’API est *incompatible au niveau ascendant*.

La conservation de la compatibilité ascendante empêche virtuellement toute modification ou ajout d’une version à l’autre, car ces changements empêchent un consommateur qui cible une version ultérieure de s’exécuter sous une version antérieure. Les développeurs s’attendent à ce qu’un consommateur qui s’appuie sur une API plus récente ne puisse ne pas fonctionner correctement avec l’API plus ancienne.

La conservation de la compatibilité ascendante n’est pas un objectif de .NET Core.

## <a name="see-also"></a>Voir aussi

- [Évaluer les changements cassants dans .NET Core](index.md)
