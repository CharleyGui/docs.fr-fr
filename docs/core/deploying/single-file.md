---
title: Application à fichier unique
description: Découvrez ce qu’est une application à fichier unique et pourquoi envisager d’utiliser ce modèle de déploiement d’application.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495798"
---
# <a name="single-file-deployment-and-executable"></a>Déploiement et exécutable d’un seul fichier

L’empaquetage de tous les fichiers dépendants de l’application dans un seul fichier binaire fournit à un développeur d’applications l’option intéressante pour déployer et distribuer l’application en tant que fichier unique. Ce modèle de déploiement est disponible depuis .NET Core 3,0 et a été amélioré dans .NET 5,0. Précédemment dans .NET Core 3,0, lorsqu’un utilisateur exécute votre application à fichier unique, l’hôte .NET Core extrait d’abord tous les fichiers dans un répertoire temporaire avant d’exécuter l’application. .NET 5,0 améliore cette expérience en exécutant directement le code sans avoir besoin d’extraire les fichiers de l’application.

Le déploiement d’un seul fichier est disponible pour le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) et pour les [applications autonomes](index.md#publish-self-contained). La taille du fichier unique dans une application autonome est importante, car elle inclut le runtime et les bibliothèques de Framework. L’option de déploiement de fichier unique peut être combinée avec [ReadyToRun](../tools/dotnet-publish.md) et [Trim (une fonctionnalité expérimentale dans .net 5,0) options de](trim-self-contained.md) publication.

Vous devez tenir compte de certains points à prendre en compte lors de l’utilisation d’un fichier unique, qui consiste à utiliser des informations de chemin d’accès pour localiser un fichier relatif à l’emplacement de votre application. L' <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API retourne une chaîne vide, qui est le comportement par défaut pour les assemblys chargés à partir de la mémoire. Le compilateur émet un avertissement pour cette API pendant la génération pour signaler au développeur le comportement spécifique. Si le chemin d’accès au répertoire de l’application est nécessaire, l' <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API retourne le répertoire dans lequel réside le apphost (le bundle de fichier unique lui-même). Les applications C++ managées ne conviennent pas au déploiement de fichier unique et nous vous recommandons d’écrire des applications en C# pour qu’elles soient compatibles avec un seul fichier.

Un fichier unique ne regroupe pas les bibliothèques natives par défaut. Sur Linux, nous prévoyons le runtime dans le bundle et seules les bibliothèques natives de l’application sont déployées dans le même répertoire que l’application à fichier unique. Sur Windows, nous prévoyons uniquement le code d’hébergement et les bibliothèques Runtime et application natives sont déployées dans le même répertoire que l’application à fichier unique. Cela permet de garantir une bonne expérience de débogage, qui requiert que les fichiers natifs soient exclus du fichier unique. Il existe une option pour définir un indicateur, `IncludeNativeLibrariesForSelfExtract` , pour inclure les bibliothèques natives dans le groupe de fichiers unique, mais ces fichiers seront extraits dans un répertoire temporaire de l’ordinateur client lors de l’exécution de l’application à fichier unique.

## <a name="exclude-files-from-being-embedded"></a>Exclure des fichiers de l’incorporation

Certains fichiers peuvent être explicitement exclus de l’incorporation dans le fichier unique en définissant les métadonnées suivantes :

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

Par exemple, pour placer certains fichiers dans le répertoire de publication, mais pas les regrouper dans le fichier unique :

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a>Publier une application à fichier unique-CLI

Publiez une application à fichier unique à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) . Lorsque vous publiez votre application, définissez les propriétés suivantes :

- Publier pour un Runtime spécifique : `-r win-x64`
- Publier en tant que fichier unique : `-p:PublishSingleFile=true`

L’exemple suivant publie une application pour Windows sous la forme d’une application à fichier unique autonome.

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

L’exemple suivant publie une application pour Linux sous la forme d’une application à fichier unique dépendante de l’infrastructure.

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).

## <a name="publish-a-single-file-app---visual-studio"></a>Publier une application à fichier unique-Visual Studio

Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.

01. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier. Sélectionnez **Publier**.

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .

01. Choisissez **Modifier**.

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Profil de publication Visual Studio avec le bouton modifier.":::

01. Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :

    - Définissez **le** **mode de déploiement** sur autonome.
    - Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.
    - Sélectionnez **produire un fichier unique**.

    Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Boîte de dialogue Paramètres de profil avec le mode de déploiement, le runtime cible et les options à fichier unique mis en surbrillance.":::

01. Choisissez **publier** pour publier votre application en tant que fichier unique.

Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a>Publier une application à fichier unique-Visual Studio pour Mac

Visual Studio pour Mac ne fournit pas d’options permettant de publier votre application sous la forme d’un fichier unique. Vous devez publier manuellement en suivant les instructions de la section [publication d’une application à fichier unique-CLI](#publish-a-single-file-app---cli) . Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications .net Core](index.md).
- [Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).
- [Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).
- [ `dotnet publish` commande](../tools/dotnet-publish.md).
