---
title: Couper les applications autonomes
description: Apprenez à couper les applications autonomes pour réduire leur taille. .NET Core regroupe l’heure d’exécution avec une application qui est publiée autonome et inclut généralement plus de l’exécution alors est nécessaire.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242904"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Supprimer les exécutables et les déploiements autonomes

Lors de la publication d’une application autonome, le temps d’exécution .NET Core est regroupé avec l’application. Ce regroupement ajoute une quantité importante de contenu à votre application emballée. Lorsqu’il s’agit de déployer votre application, la taille est souvent un facteur important. Garder la taille de l’application de paquet aussi petite que possible est généralement un objectif pour les développeurs d’applications.

Selon la complexité de l’application, seul un sous-ensemble de l’exécution est nécessaire pour exécuter l’application. Ces parties inutilisées du temps d’exécution ne sont pas nécessaires et peuvent être extraites de l’application emballée.

La fonction de coupe fonctionne en examinant les binaires d’application pour découvrir et construire un graphique des assemblages de temps d’exécution requis. Les assemblages restants qui ne sont pas référencés sont exclus.

> [!NOTE]
> Le rognage est une fonctionnalité expérimentale dans .NET Core 3.1 et _n’est_ disponible que pour les applications qui sont publiées autonomes.

## <a name="prevent-assemblies-from-being-trimmed"></a>Empêcher les assemblages d’être coupés

Il existe des scénarios dans lesquels la fonctionnalité de coupe ne détectera pas les références. Par exemple, lorsque la réflexion est utilisée sur un assemblage en temps d’exécution, soit par votre application, soit par une bibliothèque référencée par votre application, l’assemblage n’est pas directement référencé. Le rognage n’est pas au courant de ces références indirectes et exclurait la bibliothèque du dossier publié.

Lorsque le code fait indirectement référence à un assemblage par la réflexion, `<TrimmerRootAssembly>` vous pouvez empêcher l’assemblage d’être garni avec le réglage. L’exemple suivant montre comment `System.Security` empêcher qu’un assemblage appelé assemblage ne soit coupé :

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Coupez votre application - CLI

Coupez votre application à l’aide de la commande [de publication dotnet.](../tools/dotnet-publish.md) Lorsque vous publiez votre application, définissez les trois paramètres suivants :

- Publier comme autonome:`--self-contained true`
- Désactiver la publication à un seul fichier :`-p:PublishSingleFile=false`
- Activer l’élagage :`p:PublishTrimmed=true`

L’exemple suivant publie une application pour Windows 10 en tant qu’autonome et réduit la sortie.

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

Pour plus d’informations, voir [Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Coupez votre application - Visual Studio

Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.

01. Sur le volet **Solution Explorer,** cliquez à droite sur le projet que vous souhaitez publier. Sélectionnez **Publier...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Solution Explorer avec un menu à clic droit mettant en évidence l’option Publier.":::

    Si vous n’avez pas déjà de profil de publication, suivez les instructions pour en créer un et choisissez le type cible **Folder.**

01. Choisissez **Modifier**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Studio visuel publier le profil avec bouton d’édition.":::

01. Dans le dialogue **des paramètres de profil,** définissez les options suivantes :

    - Définissez **le mode de déploiement** en **autonome.**
    - Définissez **l’heure d’exécution de Target** à la plate-forme que vous souhaitez publier.
    - Sélectionnez **des assemblages inutilisés Trim (en avant-première).**

    Choisissez **Enregistrer** pour enregistrer les paramètres et revenir au dialogue **Publier.**

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Les paramètres de profil dialoguent avec le mode de déploiement, l’exécution cible et les options d’assemblage inutilisés mises en évidence.":::

01. Choisissez **Publier** pour publier votre application paré.

Pour plus d’informations, voir [Publier .NET Core apps avec Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Coupez votre application - Visual Studio pour Mac

Visual Studio pour Mac ne fournit pas d’options pour couper votre application lors de la publication. Vous devrez publier manuellement en suivant les instructions de la section [Trim votre application - CLI.](#trim-your-app---cli) Pour plus d’informations, voir [Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).

## <a name="see-also"></a>Voir aussi

- [.NET Déploiement d’applications de base](index.md).
- [Publier .NET Core apps avec .NET Core CLI](deploy-with-cli.md).
- [Publier des applications .NET Core avec Visual Studio](deploy-with-vs.md).
- [dotnet publier commande](../tools/dotnet-publish.md).
