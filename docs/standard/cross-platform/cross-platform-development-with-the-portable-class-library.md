---
title: Développement interplateforme avec la bibliothèque de classes portable
description: Créez des bibliothèques et des applications multiplateformes pour les plateformes Microsoft rapidement et facilement en utilisant le type de projet de bibliothèque de classes portable dans .NET.
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: be1a49f7da7ce98f9e5e3ff8d927ce5230bfa8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769143"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Développement multiplateforme avec la bibliothèque de classes portables

Le type de projet de bibliothèque de classes portables dans Visual Studio vous permet de créer rapidement et facilement des bibliothèques et des applications multiplateformes pour les plateformes Microsoft.

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

Les bibliothèques de classes portables vous aident à réduire le temps et les coûts de développement et de test du code. Utilisez ce type de projet pour écrire et générer des assemblys de .NET Framework portable, puis référencez ces assemblys à partir d’applications qui ciblent plusieurs plateformes, telles que le .NET Framework, iOS ou Mac.

Même après avoir créé un projet de bibliothèque de classes portables dans Visual Studio et commencé à le développer, vous pouvez modifier les plateformes cibles. Visual Studio compile votre bibliothèque avec les nouveaux assemblys, ce qui vous permet d’identifier les modifications que vous devez apporter dans votre code.

## <a name="create-a-portable-class-library-project"></a>Créer un projet de bibliothèque de classes portables

Pour créer une bibliothèque de classes portables, utilisez le modèle fourni dans Visual Studio. Créez un projet (**fichier**  >  **nouveau projet**) et, dans la boîte de dialogue **nouveau projet** , sélectionnez votre langage de programmation (Visual C# ou Visual Basic). Ensuite, sélectionnez le modèle **bibliothèque de classes (portable hérité)** . Entrez un nom pour votre projet, puis choisissez **OK**.

La boîte de dialogue **Ajouter une bibliothèque de classes portables** s’affiche. Choisissez au moins deux cibles, puis choisissez **OK**.

![Ajouter des cibles de bibliothèque de classes portables dans Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a>Modifier les cibles

Vous pouvez modifier les plateformes cibles d’un projet de bibliothèque de classes portable lorsque vous le créez ou après avoir démarré le développement. Si vous souhaitez modifier les cibles après avoir créé votre projet, dans **Explorateur de solutions**, ouvrez le menu contextuel de votre projet de bibliothèque de classes portable (pas la solution), puis choisissez **Propriétés**. Dans la page Propriétés du projet, l’onglet **bibliothèque** affiche les plateformes actuellement ciblées par votre projet.

![Propriétés de projet pour la bibliothèque de classes portables dans Visual Studio](media/pcl-project-properties.png)

Pour ajouter ou supprimer des cibles, cliquez sur le bouton **modifier** , puis activez et désactivez les cases à cocher appropriées.

Quand vous modifiez les cibles, les API disponibles pour le développement de votre projet changent en conséquence. Visual Studio indique les erreurs et les avertissements éventuellement engendrés par la modification des cibles.

Si vous souhaitez évaluer la portabilité de vos assemblys avant d’apporter des modifications dans Visual Studio, vous pouvez utiliser l' [Analyseur de portabilité .net](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).

## <a name="supported-types-and-members"></a>Types et membres pris en charge

Les types et les membres disponibles dans les projets de bibliothèque de classes portables dépendent de plusieurs facteurs de compatibilité :

- Ils doivent être partagés entre les cibles que vous avez sélectionnées.

- Leur comportement doit être similaire sur ces cibles.

- Ils ne doivent pas être candidats pour la dépréciation.

- Ils doivent s'avérer utiles dans un environnement portable, en particulier lorsque les membres qui les prennent en charge ne sont pas portables.

Si un membre est pris en charge dans la bibliothèque de classes portables et pour les cibles que vous avez sélectionnées, il apparaît dans votre projet dans IntelliSense. Toutefois, gardez à l'esprit que même si une API est prise en charge dans la bibliothèque de classes portables, ce sont les cibles que vous sélectionnez qui déterminent si vous pouvez utiliser cette API.

## <a name="api-differences-in-the-portable-class-library"></a>Différences d'API dans la bibliothèque de classes portables

Pour rendre les assemblys de bibliothèque de classes portables compatibles sur toutes les plateformes prises en charge, certains membres ont été légèrement modifiés dans la bibliothèque de classes portables.

## <a name="use-the-portable-class-library"></a>Utiliser la bibliothèque de classes portables

Après avoir créé votre projet de bibliothèque de classes portables, vous n'avez plus qu'à le référencer à partir d'autres projets. Vous pouvez référencer le projet ou des assemblys spécifiques qui contiennent les classes auxquelles vous souhaitez accéder.

Pour exécuter une application qui référence un assembly de bibliothèque de classes portables, la version requise (ou version ultérieure) des plateformes ciblées doit être installée sur votre ordinateur. Visual Studio contient toutes les infrastructures requises pour que vous puissiez exécuter l'application sans modification supplémentaire sur l'ordinateur que vous avez utilisé pour développer l'application.

### <a name="deploy-a-universal-windows-app"></a>Déployer une application Windows universelle

Lorsque vous créez une application Windows universelle qui fait référence à un assembly de bibliothèque de classes portable, tout ce dont vous avez besoin pour déployer l’application est inclus dans le package d’application et aucune autre étape n’est requise.

### <a name="deploy-a-net-framework-app"></a>Déployer une application .NET Framework

Quand vous déployez une application .NET Framework qui référence un assembly de bibliothèque de classes portables, vous devez spécifier une dépendance sur la version appropriée du .NET Framework. En spécifiant cette dépendance, vous êtes assuré que la version requise est installée avec votre application.

- Pour créer une dépendance avec un déploiement ClickOnce : dans **Explorateur de solutions**, choisissez le nœud de projet pour le projet que vous souhaitez publier. (Il s’agit du projet qui référence le projet de bibliothèque de classes portables.) Dans la barre de menus, **Project**choisissez  >  **Propriétés**du projet, puis choisissez l’onglet **publier** . Sur la page **publier** , choisissez **composants requis**. Sélectionnez la version requise du .NET Framework en tant que composant requis.

- Pour créer une dépendance avec un projet d’installation : dans **Explorateur de solutions**, choisissez le projet d’installation. Dans la barre de menus, choisissez Propriétés du **projet**  >  **Properties**  >  **composants requis**. Sélectionnez la version requise du .NET Framework en tant que composant requis.

Pour plus d’informations sur le déploiement d’applications .NET Framework, consultez le [Guide de déploiement pour les développeurs](../../framework/deployment/deployment-guide-for-developers.md).

## <a name="see-also"></a>Voir aussi

- [Utilisation de la bibliothèque de classes portables avec MVVM](using-portable-class-library-with-model-view-view-model.md)
- [Ressources d’application pour les bibliothèques qui ciblent plusieurs plateformes](app-resources-for-libraries-that-target-multiple-platforms.md)
- [Analyseur de portabilité .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](support-for-windows-store-apps-and-windows-runtime.md)
- [Déploiement](../../framework/deployment/net-framework-applications.md)
