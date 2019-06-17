---
title: Bien démarrer avec le .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- .NET Framework, getting started
- getting started [.NET Framework]
ms.assetid: c693fd34-88fe-4d90-b332-19eeadf3b7e7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16e20214981bb5c0f96b26f34be99026aac19266
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690186"
---
# <a name="get-started-with-the-net-framework"></a>Bien démarrer avec le .NET Framework

Le .NET Framework est un environnement d'exécution qui gère les applications ciblant le .NET Framework. Il se compose d’un Common Language Runtime qui assure la gestion de la mémoire et d’autres services système, et d’une bibliothèque de classes étendue qui permet aux programmeurs de tirer parti d’un code solide et fiable dans tous les principaux aspects du développement d'applications.

> [!NOTE] 
> Le .NET Framework est uniquement disponible sur les systèmes Windows. Vous pouvez utiliser [.NET Core](../../core/index.md) pour exécuter des applications sur Windows, MacOS et Linux. 

## <a name="Introducing"></a> Présentation de .NET Framework

Le .NET Framework est un environnement d’exécution managé pour Windows qui fournit divers services à ses applications actives. Il comporte deux composants principaux : le Common Langage Runtime (CLR) qui est le moteur d’exécution gérant les applications actives, et la bibliothèque de classes .NET Framework qui fournit une bibliothèque de code testé réutilisable que les développeurs peuvent appeler à partir de leurs propres applications. Le .NET Framework fournit notamment les services suivants aux applications en cours d’exécution :

- Gestion de la mémoire Dans de nombreux langages de programmation, les programmeurs sont chargés d'allouer et de libérer la mémoire et de gérer les durées de vie des objets. Dans les applications .NET Framework, le CLR fournit ces services de la part de l’application.

- Système de type commun. Dans les langages de programmation traditionnels, les types de base sont définis par le compilateur, ce qui complique l'interopérabilité interlangage. Dans le .NET Framework, les types de base sont définis par le système de type .NET Framework et sont communs à tous les langages qui ciblent le .NET Framework.

- Bibliothèque de classes étendue. Pour éviter d’écrire des quantités importantes de code pour gérer les opérations de programmation de bas niveau courantes, les programmeurs utilisent une bibliothèque de types et de leurs membres facilement accessible à partir de la bibliothèque de classes .NET Framework.

- Frameworks et technologies de développement. Le .NET Framework inclut des bibliothèques pour des domaines spécifiques de développement d’applications, tels qu’ASP.NET pour les applications web, ADO.NET pour l’accès aux données, Windows Communication Foundation pour les applications orientées service et Windows Presentation Foundation pour les applications bureau Windows.

- Interopérabilité des langages. Les compilateurs de langage qui ciblent le .NET Framework délivrent un code intermédiaire nommé Common Intermediate Language (CIL) qui est compilé à son tour au moment de l’exécution par le Common Language Runtime. Avec cette fonctionnalité, les routines écrites dans un langage sont accessibles à d’autres langages pour que les programmeurs se concentrent sur la création d’applications dans leurs langages préférés.

- Compatibilité des versions. À de rares exceptions près, les applications qui sont développées avec une version particulière du .NET Framework s’exécutent sans modification sur une version ultérieure.

- Exécution côte à côte. Le .NET Framework aide à résoudre les conflits de versions en permettant à plusieurs versions du Common Langage Runtime de cohabiter sur le même ordinateur. Cela signifie que plusieurs versions d'applications peuvent coexister et qu’une application peut s’exécuter sur la version du .NET Framework avec laquelle elle a été générée. L’exécution côte-à-côte s’applique aux groupes de versions .NET Framework 1.0/1.1, 2.0/3.0/3.5 et 4/4.5.x/4.6.x/4.7.x/4.8.

- Multiciblage. En ciblant [.NET Standard](../../standard/net-standard.md), les développeurs créent des bibliothèques de classes qui fonctionnent sur plusieurs plateformes .NET Framework prises en charge par cette version de la norme. Par exemple, les bibliothèques qui ciblent .NET Standard 2.0 peuvent être utilisées par des applications qui ciblent .NET Framework 4.6.1, .NET Core 2.0 et UWP 10.0.16299. 

<a name="ForUsers"></a>
## <a name="the-net-framework-for-users"></a>Le .NET Framework pour les utilisateurs

Si vous ne développez pas d’applications .NET Framework, mais que vous les utilisez, vous n’êtes pas obligé d’avoir une connaissance précise du .NET Framework ou de son exécution. Pour la plus grande part, le .NET Framework est complètement transparent aux utilisateurs.

Si vous utilisez le système d’exploitation Windows, le .NET Framework est peut-être déjà installé sur votre ordinateur. De plus, si vous installez une application qui nécessite le .NET Framework, le programme d’installation de l’application peut installer une version spécifique du .NET Framework sur votre ordinateur. Dans certains cas, vous pouvez afficher une boîte de dialogue qui vous demande d'installer le .NET Framework. Si cette boîte de dialogue apparaît quand vous essayez d’exécuter une application et que votre ordinateur a accès à Internet, vous pouvez accéder à une page web qui vous permet d’installer la version manquante du .NET Framework. Pour plus d’informations, consultez le [guide d’installation](../install/index.md).

En règle générale, vous ne devez pas désinstaller les versions du .NET Framework installées sur votre ordinateur. Il existe deux raisons à cela :

- Si une application que vous utilisez dépend d’une version spécifique du .NET Framework, elle peut cesser de fonctionner si cette version est supprimée.

- Certaines versions du .NET Framework sont des mises à jour sur place de versions antérieures. Par exemple, .NET Framework 3.5 est une mise à jour sur place de la version 2.0, et .NET Framework 4.8 est une mise à jour sur place des versions 4 à 4.7.2. Pour plus d’informations, consultez [Versions et dépendances du .NET Framework](../migration-guide/versions-and-dependencies.md).

Sur les versions Windows antérieures à Windows 8, si vous choisissez de supprimer le .NET Framework, désinstallez-le toujours à l’aide de l’option **Programmes et fonctionnalités** du Panneau de configuration. Ne supprimez jamais manuellement une version du .NET Framework. Sur Windows 8 et versions ultérieures, le .NET Framework est un composant du système d’exploitation qui ne peut pas être désinstallé séparément.

Notez que plusieurs versions du .NET Framework peuvent coexister simultanément sur un même ordinateur. Cela signifie que vous n’avez pas besoin de désinstaller les versions antérieures afin d’installer une version ultérieure.

## <a name="ForDevelopers"></a> Le .NET Framework pour les développeurs

Si vous êtes développeur, choisissez n’importe quel langage de programmation prenant en charge le .NET Framework pour créer vos applications. Comme le .NET Framework fournit l’indépendance et l’interopérabilité des langages, vous interagissez avec d’autres applications et composants .NET Framework, quel que soit le langage utilisé pour leur développement.

Pour développer des applications ou des composants .NET Framework, procédez comme suit :

1. Si elle n’est pas préinstallée sur votre système d’exploitation, installez la version du .NET Framework ciblée par votre application. La version de production la plus récente est le .NET Framework 4.8. Elle est préinstallée sur la Mise à jour de mai 2019 de Windows 10 et elle est disponible en téléchargement sur les versions précédentes du système d’exploitation Windows. Pour la configuration système requise du .NET Framework, consultez [Configuration requise](system-requirements.md). Pour plus d’informations sur l’installation d’autres versions du .NET Framework, consultez [Guide d’installation](../install/guide-for-developers.md). Les autres packages .NET Framework sont fournis hors bande, ce qui signifie qu’ils sont publiés en continu, en dehors d’un cycle de publications classique ou planifié. Pour plus d’informations sur ces packages, consultez [Versions finales hors plage du .NET Framework](the-net-framework-and-out-of-band-releases.md).

2. Sélectionnez le ou les langages pris en charge par le .NET Framework que vous prévoyez d’utiliser pour développer vos applications. Microsoft propose plusieurs langages, notamment [Visual Basic](../../visual-basic/index.md), [C#](../../csharp/index.md), [F#](../../fsharp/index.md) et [C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp). (Un langage de programmation qui vous permet de développer des applications pour le .NET Framework respecte la [spécification CLI (Common Language Infrastructure)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/).)

3. Sélectionnez et installez l’environnement de développement à utiliser pour créer vos applications et qui prend en charge le ou les langages de programmation sélectionnés. L’environnement de développement intégré (IDE) de Microsoft pour les applications .NET Framework est [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Il est disponible dans plusieurs éditions.

Pour plus d’informations sur le développement d’applications qui ciblent le .NET Framework, consultez le [Guide de développement](../development-guide.md).

## <a name="related-articles"></a>Articles connexes

| Titre | Description |
| ----- |------------ |
| [Vue d’ensemble](overview.md) | Fournit des informations détaillées pour les développeurs qui créent des applications ciblant le .NET Framework. |
| [Guide d’installation](../install/index.md) | Fournit des informations sur l'installation du .NET Framework. |  
| [Versions finales hors plage de .NET Framework](the-net-framework-and-out-of-band-releases.md) | Décrit les versions release hors bande du .NET Framework et leur utilisation dans votre application. |
| [Configuration système requise](system-requirements.md) | Répertorie les configurations matérielle et logicielle requises pour exécuter le .NET Framework. |
| [.NET Core et Open-Source](net-core-and-open-source.md) | Décrit le .NET Core en rapport avec le .NET Framework et comment accéder aux projets .NET Core open source. |
| [Documentation .NET Core](../../core/index.md) | Fournit la documentation de référence sur les concepts et les API de .NET Core. |
| [.NET Standard](../../standard/net-standard.md) | Traite de .NET Standard, une spécification avec version prise en charge par les implémentations .NET individuelles afin de garantir la disponibilité d’un ensemble cohérent d’API sur plusieurs plateformes.

## <a name="see-also"></a>Voir aussi

- [Guide du .NET Framework](../index.md)
- [Nouveautés](../whats-new/index.md)
- [Navigateur d’API .NET](../../../api/index.md)
- [Guide de développement](../development-guide.md)
