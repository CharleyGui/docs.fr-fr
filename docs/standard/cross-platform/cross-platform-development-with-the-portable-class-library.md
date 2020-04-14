---
title: Développement interplateforme avec la bibliothèque de classes portable
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242801"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Développement multiplateforme avec la Bibliothèque de classe portable

Le type de projet portable Class Library dans Visual Studio vous aide à créer des applications et des bibliothèques multiplateformes pour les plates-formes Microsoft rapidement et facilement.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Les bibliothèques de classes portables vous aident à réduire le temps et les coûts de développement et de test du code. Utilisez ce type de projet pour écrire et construire des assemblages cadres .NET portables, puis référencez ces assemblages à partir d’applications qui ciblent plusieurs plates-formes telles que le cadre .NET, iOS ou Mac.

Même après avoir créé un projet de bibliothèque de classes portables dans Visual Studio et commencé à le développer, vous pouvez modifier les plateformes cibles. Visual Studio compile votre bibliothèque avec les nouveaux assemblages, ce qui vous aide à identifier les modifications que vous devez apporter dans votre code.

## <a name="create-a-portable-class-library-project"></a>Créer un projet de bibliothèque de classe portable

Pour créer une bibliothèque de classe portable, utilisez le modèle fourni dans Visual Studio. Créez un nouveau projet **(File** > **New Project**), et dans la boîte de dialogue du nouveau **projet,** sélectionnez votre langage de programmation (Visual CMD ou Visual Basic). Ensuite, sélectionnez le modèle **De la bibliothèque de classe (Legacy Portable).** Entrez un nom pour votre projet et choisissez **OK**.

La boîte de dialogue **Add Portable Class Library** apparaît. Choisissez deux cibles ou plus, puis choisissez **OK**.

![Ajouter des cibles de bibliothèque de classe portables dans Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Modifier les objectifs

Vous pouvez modifier les plates-formes cibles d’un projet de bibliothèque de classe portable lorsque vous le créez ou après avoir commencé à développer. Si vous souhaitez modifier les cibles après avoir créé votre projet, dans **Solution Explorer,** ouvrez le menu raccourci pour votre projet de bibliothèque de classe portable (pas la solution), puis choisissez **des propriétés**. Sur la page propriétés du projet, l’onglet **Bibliothèque** affiche les plates-formes que votre projet cible actuellement.

![Propriétés de projet pour la bibliothèque de classe portable dans Visual Studio](media/pcl-project-properties.png)

Pour ajouter ou supprimer les cibles, choisissez le bouton **Modifier,** puis sélectionnez et effacez les cases à cocher appropriées.

Quand vous modifiez les cibles, les API disponibles pour le développement de votre projet changent en conséquence. Visual Studio indique les erreurs et les avertissements éventuellement engendrés par la modification des cibles.

Si vous souhaitez évaluer la portabilité de vos assemblages avant d’apporter des modifications dans Visual Studio, vous pouvez utiliser [l’analyseur de portabilité .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Types et membres pris en charge

Les types et les membres disponibles dans les projets de bibliothèque de classes portables dépendent de plusieurs facteurs de compatibilité :

- Ils doivent être partagés entre les cibles que vous avez sélectionnées.

- Leur comportement doit être similaire sur ces cibles.

- Ils ne doivent pas être candidats pour la dépréciation.

- Ils doivent s'avérer utiles dans un environnement portable, en particulier lorsque les membres qui les prennent en charge ne sont pas portables.

Si un membre est pris en charge dans la bibliothèque de classes portables et pour les cibles que vous avez sélectionnées, il apparaît dans votre projet dans IntelliSense. Toutefois, gardez à l'esprit que même si une API est prise en charge dans la bibliothèque de classes portables, ce sont les cibles que vous sélectionnez qui déterminent si vous pouvez utiliser cette API.

## <a name="api-differences-in-the-portable-class-library"></a>Différences d'API dans la bibliothèque de classes portables

Pour rendre les assemblys de bibliothèque de classes portables compatibles sur toutes les plateformes prises en charge, certains membres ont été légèrement modifiés dans la bibliothèque de classes portables.

## <a name="use-the-portable-class-library"></a>Utiliser la bibliothèque de classe portable

Après avoir créé votre projet de bibliothèque de classes portables, vous n'avez plus qu'à le référencer à partir d'autres projets. Vous pouvez référencer le projet ou des assemblys spécifiques qui contiennent les classes auxquelles vous souhaitez accéder.

Pour exécuter une application qui référence un assembly de bibliothèque de classes portables, la version requise (ou version ultérieure) des plateformes ciblées doit être installée sur votre ordinateur. Visual Studio contient toutes les infrastructures requises pour que vous puissiez exécuter l'application sans modification supplémentaire sur l'ordinateur que vous avez utilisé pour développer l'application.

### <a name="deploy-a-universal-windows-app"></a>Déployer une application Windows universelle

Lorsque vous créez une application Windows universelle qui fait référence à un assemblage de bibliothèque de classe portable, tout ce dont vous avez besoin pour déployer l’application est inclus dans le paquet d’applications, et aucune autre étape n’est nécessaire.

### <a name="deploy-a-net-framework-app"></a>Déployer une application cadre .NET

Quand vous déployez une application .NET Framework qui référence un assembly de bibliothèque de classes portables, vous devez spécifier une dépendance sur la version appropriée du .NET Framework. En spécifiant cette dépendance, vous êtes assuré que la version requise est installée avec votre application.

- Pour créer une dépendance avec le déploiement ClickOnce: In **Solution Explorer**, choisissez le nœud de projet pour le projet que vous souhaitez publier. (C’est le projet qui fait référence au projet de bibliothèque de classe portable.) Sur la barre de menu, choisissez **Project** > **Properties,** puis choisissez l’onglet **Publier.** Sur la page **Publier,** choisissez **Préalables**. Sélectionnez la version requise du .NET Framework en tant que composant requis.

- Pour créer une dépendance avec un projet d’installation: Dans **Solution Explorer**, choisissez le projet d’installation. Sur la barre de menu, choisissez **Project** > **Properties** > **Prerequisites**. Sélectionnez la version requise du .NET Framework en tant que composant requis.

Pour plus d’informations sur le déploiement d’applications cadre .NET, voir [Guide de déploiement pour les développeurs](../../../docs/framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Voir aussi

- [Utilisation de la bibliothèque de classes portables avec MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Ressources d’applications pour les bibliothèques qui ciblent plusieurs plates-formes](app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analyseur de portabilité .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [Déploiement](../../../docs/framework/deployment/net-framework-applications.md)
