---
title: Guide de style F#
description: 'Découvrez les cinq principes du bon code F #.'
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223653"
---
# <a name="f-style-guide"></a>Guide de style F#

Les articles suivants décrivent les instructions de mise en forme du code F # et des conseils relatifs aux fonctionnalités du langage et à la façon dont ils doivent être utilisés.

Cette recommandation a été formulée en fonction de l’utilisation de F # dans les bases de code volumineuses avec un groupe diversifié de programmeurs. Ce guide est généralement destiné à la réussite de l’utilisation de F # et minimise les frustrations lorsque les exigences relatives aux programmes évoluent au fil du temps.

## <a name="five-principles-of-good-f-code"></a>Cinq principes de bon code F #

Gardez à l’esprit les principes suivants à chaque fois que vous écrivez du code F #, en particulier dans les systèmes qui évoluent au fil du temps. Chaque élément d’aide dans d’autres articles provient de ces cinq points.

1. **Un bon code F # est concis, expressif et composable**

    F # comporte de nombreuses fonctionnalités qui vous permettent d’exprimer des actions dans moins de lignes de code et de réutiliser les fonctionnalités génériques. La bibliothèque principale F # contient également de nombreux types et fonctions utiles pour utiliser des collections de données communes. La composition de vos propres fonctions et de celles de la bibliothèque principale F # (ou d’autres bibliothèques) fait partie de la programmation idiomatique F # de routine. En règle générale, si vous pouvez exprimer une solution à un problème dans moins de lignes de code, d’autres développeurs (ou votre propre à l’avenir) seront gain appréciables. Il est également fortement recommandé d’utiliser une bibliothèque telle que FSharp. Core, les nombreuses [bibliothèques .net](../../../api/index.md) sur lesquelles s’exécute F # ou un package tiers sur [NuGet](https://www.nuget.org/) lorsque vous devez effectuer une tâche non triviale.

2. **Un bon code F # est interopérable**

    L’interopérabilité peut prendre plusieurs formes, notamment la consommation de code dans différents langages. Les limites de votre code avec lesquelles d’autres appelants interagissent sont des éléments essentiels pour se rendre corrects, même si les appelants sont également en F #. Lors de l’écriture de F #, vous devez toujours réfléchir à la façon dont un autre code appellera dans le code que vous écrivez, y compris s’il le fait à partir d’un autre langage tel que C#. Les [instructions de conception des composants F #](component-design-guidelines.md) décrivent en détail l’interopérabilité.

3. **Un bon code F # utilise la programmation d’objets, et non l’orientation de l’objet**

    F # offre une prise en charge complète de la programmation avec des objets dans .NET, y compris les [classes](../language-reference/classes.md), les [interfaces](../language-reference/interfaces.md), les [modificateurs d’accès](../language-reference/access-control.md), les [classes abstraites](../language-reference/abstract-classes.md), etc. Pour le code fonctionnel plus complexe, tel que les fonctions qui doivent être compatibles avec le contexte, les objets peuvent facilement encapsuler des informations contextuelles dans des méthodes qui ne le permettent pas. Les fonctionnalités telles que les [paramètres facultatifs](../language-reference/members/methods.md#optional-arguments) et l’utilisation soigneuse de la [surcharge](../language-reference/members/methods.md#overloaded-methods) peuvent rendre la consommation de cette fonctionnalité plus facile pour les appelants.

4. **Un bon code F # fonctionne correctement sans avoir à exposer la mutation**

    Il n’est pas secret d’écrire du code à hautes performances. vous devez utiliser la mutation. C’est le mode de fonctionnement des ordinateurs, après tout. Ce code est souvent sujet aux erreurs et difficile à trouver. Évitez d’exposer la mutation aux appelants. Au lieu de cela, [créez une interface fonctionnelle qui masque une implémentation basée sur une mutation lorsque les](conventions.md#performance) performances sont critiques.

5. **Un bon code F # est outil**

    Les outils sont très utiles pour travailler dans des codes base volumineux et vous pouvez écrire du code F # de manière à ce qu’il puisse être utilisé plus efficacement avec les outils de langage F #. Un exemple consiste à s’assurer que vous ne le abuser pas avec un style de programmation à POINTER libre, afin que les valeurs intermédiaires puissent être inspectées à l’aide d’un débogueur. Un autre exemple utilise des [Commentaires de documentation XML](../language-reference/xml-documentation.md) décrivant les constructions de telle sorte que les info-bulles des éditeurs puissent afficher ces commentaires sur le site d’appel. Réfléchissez toujours à la façon dont votre code sera lu, parcouru, débogué et manipulé par d’autres programmeurs avec leurs outils.

## <a name="next-steps"></a>Étapes suivantes

Les [instructions de mise en forme du code F #](formatting.md) fournissent des conseils sur la façon de mettre en forme le code afin qu’il soit facile à lire.

Les [conventions de codage f #](conventions.md) fournissent des conseils pour les idiomes de programmation f # qui aident à effectuer la maintenance à long terme des codes base f # plus volumineux.

Les [instructions de conception des composants f #](component-design-guidelines.md) fournissent des conseils pour la création de composants f #, tels que des bibliothèques.
