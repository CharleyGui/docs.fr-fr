---
title: Guide de style F#
description: Apprenez les cinq principes d’un bon code F.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400266"
---
# <a name="f-style-guide"></a>Guide de style F#

Les articles suivants décrivent des lignes directrices pour le formatage du code F et des conseils d’actualité pour les caractéristiques de la langue et la façon dont elles doivent être utilisées.

Ces directives ont été formulées en fonction de l’utilisation de FMD dans de grandes bases de code avec un groupe diversifié de programmeurs. Ces lignes directrices mènent généralement à l’utilisation réussie de F et minimise les frustrations lorsque les exigences pour les programmes changent au fil du temps.

## <a name="five-principles-of-good-f-code"></a>Cinq principes de bon code F

Gardez à l’esprit les principes suivants chaque fois que vous écrivez du code F, en particulier dans les systèmes qui changeront au fil du temps. Chaque élément d’orientation dans d’autres articles provient de ces cinq points.

1. **Un bon code F est succinct, expressif et composable**

    F a de nombreuses fonctionnalités qui vous permettent d’exprimer des actions dans moins de lignes de code et de réutiliser la fonctionnalité générique. La bibliothèque de base de FMD contient également de nombreux types et fonctions utiles pour travailler avec des collections communes de données. La composition de vos propres fonctions et de celles de la bibliothèque de base de F (ou d’autres bibliothèques) fait partie de la programmation Idiomatique de routine de F. En règle générale, si vous pouvez exprimer une solution à un problème dans moins de lignes de code, d’autres développeurs (ou votre futur soi) seront reconnaissants. Il est également fortement recommandé d’utiliser une bibliothèque comme FSharp.Core, les [vastes bibliothèques .NET](../../../api/index.md) que F ' fonctionne sur, ou un paquet tiers sur [NuGet](https://www.nuget.org/) lorsque vous avez besoin de faire une tâche non-trivial.

2. **Un bon code F est interopérable**

    L’interopération peut prendre plusieurs formes, y compris la consommation de code dans différentes langues. Les limites de votre code avec lesquelles les autres appelants interopérent sont des éléments essentiels pour obtenir le droit, même si les appelants sont également en F. Lors de l’écriture de F, vous devriez toujours penser à la façon dont d’autres codes vont appeler dans le code que vous écrivez, y compris s’ils le font à partir d’une autre langue comme C. Les lignes directrices sur [la conception des composants FMD](component-design-guidelines.md) décrivent en détail l’interopérabilité.

3. **Un bon code FMD utilise la programmation d’objets, et non l’orientation de l’objet**

    F a un soutien complet pour la programmation avec des objets en .NET, y compris [les classes,](../language-reference/classes.md) [interfaces](../language-reference/interfaces.md), [modificateurs d’accès](../language-reference/access-control.md), [classes abstraites](../language-reference/abstract-classes.md), et ainsi de suite. Pour un code fonctionnel plus compliqué, comme les fonctions qui doivent être contextuelles, les objets peuvent facilement encapsuler des informations contextuelles d’une manière qui fonctionne. Des fonctionnalités telles que des [paramètres facultatifs](../language-reference/members/methods.md#optional-arguments) et une utilisation minutieuse de [la surcharge](../language-reference/members/methods.md#overloaded-methods) peuvent faciliter la consommation de cette fonctionnalité pour les appelants.

4. **Un bon code FMD fonctionne bien sans exposer la mutation**

    Ce n’est un secret pour personne que pour écrire du code haute performance, vous devez utiliser la mutation. C’est comme ça que fonctionnent les ordinateurs, après tout. Un tel code est souvent sujet aux erreurs et difficile à obtenir à droite. Évitez d’exposer la mutation aux appelants. Au lieu de cela, [construire une interface fonctionnelle qui cache une implémentation basée sur la mutation](conventions.md#performance) lorsque les performances sont critiques.

5. **Un bon code F est outilable**

    Les outils sont inestimables pour travailler dans de grandes bases de code, et vous pouvez écrire du code F de telle sorte qu’il puisse être utilisé plus efficacement avec l’outillage linguistique F. Un exemple est de s’assurer que vous n’en faites pas trop avec un style de programmation sans point, de sorte que les valeurs intermédiaires peuvent être inspectées avec un débbuggeur. Un autre exemple est l’utilisation de [commentaires de documentation XML](../language-reference/xml-documentation.md) décrivant des constructions telles que les outils dans les éditeurs peuvent afficher ces commentaires sur le site d’appel. Réfléchissez toujours à la façon dont votre code sera lu, navigué, débogé et manipulé par d’autres programmeurs avec leurs outils.

## <a name="next-steps"></a>Étapes suivantes

Les lignes directrices de [formatage du code FMD](formatting.md) fournissent des conseils sur la façon de formater le code afin qu’il soit facile à lire.

Les [conventions de codage FMD](conventions.md) fournissent des conseils pour les idiomes de programmation de FMD qui aideront à maintenir à long terme de plus grandes bases de code F.

Les lignes directrices sur [la conception des composants FMD](component-design-guidelines.md) fournissent des conseils pour la rédaction de composants F, tels que les bibliothèques.
