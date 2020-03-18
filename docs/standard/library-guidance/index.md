---
title: Conseils sur la bibliothèque .NET open source
description: Recommandations de bonne pratique à l’attention des développeurs qui créent des bibliothèques .NET de qualité.
ms.date: 10/17/2018
ms.openlocfilehash: 4c76dfae6ffc39df7f15381be64e33657067d79d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731423"
---
# <a name="open-source-library-guidance"></a>Conseils sur la bibliothèque open source

Cette aide fournit des recommandations à l’attention des développeurs qui créent des bibliothèques .NET de qualité. Cette documentation se concentre sur le *quoi* et le *pourquoi* de la création d’une bibliothèque .NET, mais pas sur le *comment*.

Aspects des bibliothèques .NET open source de qualité :

> [!div class="checklist"]
>
> * **Inclusives** - Les bonnes bibliothèques .NET s’efforcent de prendre en charge plusieurs plateformes, langages de programmation et applications.
> * **Stables** - Les bonnes bibliothèques .NET coexistent dans l’écosystème .NET en s’exécutant dans les applications créées avec de nombreuses bibliothèques.
> * **Conçues pour évoluer** - Les bibliothèques .NET doivent s’améliorer et évoluer au fil du temps tout en prenant en charge les utilisateurs existants.
> * **Débogables** - Les bibliothèques .NET doivent utiliser les derniers outils afin de créer une excellente expérience de débogage pour les utilisateurs.
> * **Approuvées** - Les bibliothèques .NET ont la confiance des développeurs en publiant sur NuGet à l’aide des bonnes pratiques de sécurité.

> [!div class="nextstepaction"]
> [Découvrir](./get-started.md)

## <a name="types-of-recommendations"></a>Types de suggestions

Chaque article présente quatre types de suggestions : **À faire**, **Envisager**, **Éviter** et **À ne pas faire**. Le type de suggestion indique si celle-ci doit être suivie ou pas.

Vous devez presque toujours suivre une suggestion **À faire**. Par exemple :

✔️ À FAIRE : Distribuer votre bibliothèque à l’aide d’un package NuGet.

En revanche, les recommandations **Envisager** doivent généralement être appliquées, mais il existe des exceptions à la règle qui sont fondées, c’est pourquoi vous ne devez pas vous inquiéter si vous ne les suivez pas :

✔️ ENVISAGER d’utiliser [SemVer 2.0.0](https://semver.org/) pour versionner votre package NuGet.

Les suggestions **Éviter** indiquent quelque chose qui n’est généralement pas une bonne idée, mais enfreindre les règles peut parfois avoir du sens :

❌AVOID NuGet références paquet qui exigent une version exacte.

Et enfin, les suggestions **À ne pas faire** désignent quelque chose que vous ne devez presque jamais faire :

❌NE publiez PAS de versions de votre bibliothèque, nommées en force et non. Par exemple, `Contoso.Api` et `Contoso.Api.StrongNamed`.

>[!div class="step-by-step"]
>[Suivant](get-started.md)
