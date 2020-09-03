---
title: Bien démarrer avec le .NET Framework
description: Prise en main de .NET, qui est un environnement d’exécution de Runtime qui gère les applications. Il contient une common language runtime (CLR) et une bibliothèque de classes étendue.
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
ms.openlocfilehash: 85ba856fd695f264f75a6dab2dca3aded4e5cdc1
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414966"
---
# <a name="get-started-with-net-framework"></a>Prise en main de .NET Framework

.NET Framework est un environnement d’exécution qui gère les applications qui ciblent .NET Framework. Il se compose d’un Common Language Runtime qui assure la gestion de la mémoire et d’autres services système, et d’une bibliothèque de classes étendue qui permet aux programmeurs de tirer parti d’un code solide et fiable dans tous les principaux aspects du développement d'applications.

> [!NOTE]
> .NET Framework est disponible uniquement sur les systèmes Windows. Vous pouvez utiliser [.net Core](../../core/introduction.md) pour développer et exécuter des applications sur Windows, MacOS et Linux.

## <a name="what-is-net-framework"></a>Qu’est-ce que .NET Framework ?

.NET Framework est un environnement d’exécution géré pour Windows qui fournit divers services à ses applications en cours d’exécution. Il comporte deux composants principaux : le Common Langage Runtime (CLR) qui est le moteur d’exécution gérant les applications actives, et la bibliothèque de classes .NET Framework qui fournit une bibliothèque de code testé réutilisable que les développeurs peuvent appeler à partir de leurs propres applications. Les services fournis par .NET Framework à l’exécution d’applications sont les suivants :

- Gestion de la mémoire Dans de nombreux langages de programmation, les programmeurs sont chargés d'allouer et de libérer la mémoire et de gérer les durées de vie des objets. Dans les applications .NET Framework, le CLR fournit ces services de la part de l’application.

- Système de type commun. Dans les langages de programmation traditionnels, les types de base sont définis par le compilateur, ce qui complique l'interopérabilité interlangage. Dans .NET Framework, les types de base sont définis par le système de type .NET Framework et sont communs à tous les langages qui ciblent .NET Framework.

- Bibliothèque de classes étendue. Pour éviter d’écrire des quantités importantes de code pour gérer les opérations de programmation de bas niveau courantes, les programmeurs utilisent une bibliothèque de types et de leurs membres facilement accessible à partir de la bibliothèque de classes .NET Framework.

- Infrastructures et technologies de développement. .NET Framework comprend des bibliothèques pour des domaines spécifiques de développement d’applications, tels que ASP.NET pour les applications Web, ADO.NET pour l’accès aux données, les Windows Communication Foundation pour les applications orientées service et les Windows Presentation Foundation pour les applications de bureau Windows.

- Interopérabilité des langages. Les compilateurs de langage qui ciblent .NET Framework émettent un code intermédiaire nommé Common Intermediate Language (CIL), qui est compilé à son tour au moment de l’exécution par le common language runtime. Avec cette fonctionnalité, les routines écrites dans un langage sont accessibles à d’autres langages pour que les programmeurs se concentrent sur la création d’applications dans leurs langages préférés.

- Compatibilité des versions. À de rares exceptions près, les applications développées à l’aide d’une version particulière de .NET Framework s’exécutent sans modification sur une version ultérieure.

- Exécution côte à côte. .NET Framework permet de résoudre les conflits de versions en permettant à plusieurs versions du common language runtime d’exister sur le même ordinateur. Cela signifie que plusieurs versions d’applications peuvent coexister et qu’une application peut s’exécuter sur la version de .NET Framework avec laquelle elle a été générée. L’exécution côte-à-côte s’applique aux groupes de versions .NET Framework 1.0/1.1, 2.0/3.0/3.5 et 4/4.5.x/4.6.x/4.7.x/4.8.

- Multiciblage. En ciblant [.NET Standard](../../standard/net-standard.md), les développeurs créent des bibliothèques de classes qui fonctionnent sur plusieurs plateformes .NET Framework prises en charge par cette version de la norme. Par exemple, les bibliothèques qui ciblent .NET Standard 2,0 peuvent être utilisées par les applications qui ciblent .NET Framework 4.6.1, .NET Core 2,0 et UWP 10.0.16299.

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Le .NET Framework pour les utilisateurs

Si vous ne développez pas d’applications .NET Framework, mais que vous les utilisez, vous n’êtes pas obligé d’avoir des connaissances spécifiques sur .NET Framework ou son fonctionnement. Pour l’essentiel, le Framework est totalement transparent pour les utilisateurs.

Si vous utilisez le système d’exploitation Windows, .NET Framework peut déjà être installé sur votre ordinateur. En outre, si vous installez une application qui requiert .NET Framework, le programme d’installation de l’application peut installer une version spécifique du Framework sur votre ordinateur. Dans certains cas, une boîte de dialogue s’affiche pour vous demander d’installer .NET Framework. Si vous venez d’essayer d’exécuter une application lorsque cette boîte de dialogue apparaît et que votre ordinateur a accès à Internet, vous pouvez accéder à une page Web qui vous permet d’installer la version manquante de .NET Framework. Pour plus d’informations, consultez le [Guide d’installation](../install/index.md).

En général, vous ne devez pas désinstaller les versions de .NET Framework installées sur votre ordinateur. Il existe deux raisons à cela :

- Si une application que vous utilisez dépend d’une version spécifique de .NET Framework, cette application peut s’arrêter si cette version est supprimée.

- Certaines versions de .NET Framework sont des mises à jour sur place des versions antérieures. Par exemple, .NET Framework 3,5 est une mise à jour sur place de la version 2,0, et .NET Framework 4,8 est une mise à jour sur place des versions 4 à 4.7.2. Pour plus d’informations, consultez [Versions et dépendances du .NET Framework](../migration-guide/versions-and-dependencies.md).

Dans les versions de Windows antérieures à Windows 8, si vous choisissez de supprimer .NET Framework, utilisez toujours **programmes et fonctionnalités** dans le panneau de configuration pour le désinstaller. Ne supprimez jamais une version de .NET Framework manuellement. Sur Windows 8 et versions ultérieures, .NET Framework est un composant du système d’exploitation et ne peut pas être désinstallé séparément.

Plusieurs versions de .NET Framework peuvent coexister sur un seul ordinateur en même temps. Cela signifie que vous n’avez pas besoin de désinstaller les versions antérieures afin d’installer une version ultérieure.

## <a name="net-framework-for-developers"></a>.NET Framework pour les développeurs

Si vous êtes développeur, choisissez un langage de programmation qui prend en charge .NET Framework pour créer vos applications. Étant donné que .NET Framework fournit l’indépendance et l’interopérabilité des langages, vous interagissez avec d’autres applications et composants .NET Framework, quel que soit le langage dans lequel ils ont été développés.

Pour développer des applications ou des composants .NET Framework, procédez comme suit :

1. Si elle n’est pas préinstallée sur votre système d’exploitation, installez la version de .NET Framework que votre application ciblera. La version de production la plus récente est .NET Framework 4,8. Il est préinstallé sur Windows 10 2019 Update et peut être téléchargé sur des versions antérieures du système d’exploitation Windows. Pour la configuration système requise du .NET Framework, consultez [Configuration requise](system-requirements.md). Pour plus d’informations sur l’installation d’autres versions de .NET Framework, consultez le [Guide d’installation](../install/guide-for-developers.md). Les autres packages .NET Framework sont fournis hors bande, ce qui signifie qu’ils sont publiés en continu, en dehors d’un cycle de publications classique ou planifié. Pour plus d’informations sur ces packages, consultez [versions .NET Framework et hors plage](the-net-framework-and-out-of-band-releases.md).

2. Sélectionnez la ou les langues prises en charge par la version de .NET Framework que vous avez l’intention d’utiliser pour développer vos applications. Microsoft propose plusieurs langages, notamment [Visual Basic](../../visual-basic/index.yml), [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml) et [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp). (Un langage de programmation qui vous permet de développer des applications pour .NET Framework adhère à la [spécification Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).)

3. Sélectionnez et installez l’environnement de développement à utiliser pour créer vos applications et qui prend en charge le ou les langages de programmation sélectionnés. L’environnement de développement intégré (IDE) de Microsoft pour les applications .NET Framework est [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Il est disponible dans plusieurs éditions.

Pour plus d’informations sur le développement d’applications qui ciblent des .NET Framework, consultez le [Guide de développement](../development-guide.md).

## <a name="related-articles"></a>Articles connexes

| Intitulé | Description |
| ----- |------------ |
| [Vue d'ensemble](overview.md) | Fournit des informations détaillées pour les développeurs qui créent des applications ciblant .NET Framework. |
| [Guide d'installation](../install/index.md) | Fournit des informations sur l’installation de .NET Framework. |  
| [Versions .NET Framework et hors plage](the-net-framework-and-out-of-band-releases.md) | Décrit les versions finales hors plage du .NET Framework et leur utilisation dans votre application. |
| [Configuration requise](system-requirements.md) | Répertorie la configuration matérielle et logicielle requise pour l’exécution de .NET Framework. |
| [.NET Core et Open-Source](net-core-and-open-source.md) | Décrit .NET Core par rapport à .NET Framework et comment accéder aux projets .NET Core Open source. |
| [Documentation .NET Core](../../core/introduction.md) | Fournit la documentation de référence sur les concepts et les API de .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | Décrit .NET Standard, une spécification avec version que les implémentations de .NET individuelles prennent en charge pour garantir qu’un ensemble cohérent d’API est disponible sur plusieurs plateformes.

## <a name="see-also"></a>Voir aussi

- [Guide .NET Framework](../index.yml)
- [Nouveautés](../whats-new/index.md)
- [Navigateur d’API .NET](../../../api/index.md)
- [Guide de développement](../development-guide.md)
