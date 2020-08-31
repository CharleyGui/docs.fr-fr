---
title: Découper les applications autonomes
description: Découvrez comment supprimer les applications autonomes pour réduire leur taille. .NET Core regroupe le Runtime avec une application qui est publiée automatiquement et qui comprend généralement un plus grand nombre d’exécutions.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 7a4731e2cbaa3835e6aa6ba558dfa8cd03828e01
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053105"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Supprimer les exécutables et les déploiements autonomes

Le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) est le modèle de déploiement le plus performant depuis la création de .net. Dans ce scénario, le développeur d’applications ne regroupe que l’application et les assemblys tiers dans l’attente que le Runtime .NET et les bibliothèques d’infrastructure soient disponibles sur l’ordinateur client. Ce modèle de déploiement est toujours le plus dominant dans .NET Core, mais dans certains scénarios, le modèle dépendant du Framework n’est pas optimal. L’alternative consiste à publier une [application autonome](index.md#publish-self-contained), où le Runtime .net Core et l’infrastructure sont regroupés avec l’application et les assemblys tiers.

Le modèle Trim-self-contained Deployment est une version spécialisée du modèle de déploiement autonome qui est optimisé pour réduire la taille du déploiement. La réduction de la taille du déploiement est une condition essentielle pour certains scénarios côté client comme les applications éblouissantes. En fonction de la complexité de l’application, seul un sous-ensemble des assemblys de l’infrastructure est référencé et un sous-ensemble du code dans chaque assembly est requis pour exécuter l’application. Les parties inutilisées des bibliothèques ne sont pas nécessaires et peuvent être supprimées de l’application empaquetée.

Toutefois, il existe un risque que l’analyse du temps de génération de l’application puisse provoquer des échecs lors de l’exécution, en raison de l’impossibilité d’analyser de manière fiable divers modèles de code problématiques (principalement centrés sur l’utilisation de la réflexion). Étant donné que la fiabilité ne peut pas être garantie, ce modèle de déploiement est proposé sous la forme d’une fonctionnalité en version préliminaire.

Le moteur d’analyse de la durée de génération fournit des avertissements au développeur de modèles de code problemmatic pour détecter les autres codes requis. Le code peut être annoté avec des attributs pour indiquer au massicot les autres éléments à inclure. De nombreux modèles de réflexion peuvent être remplacés par la génération de code au moment de la génération à l’aide de [générateurs de source](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).

Le mode de découpage des applications est configuré avec le `TrimMode` paramètre. La valeur par défaut est `copyused` et regroupe les assemblys référencés avec l’application. La `link` valeur est utilisée avec les applications de Webassembly éblouissantes et supprime le code inutilisé dans les assemblys. Les avertissements d’analyse de suppression fournissent des informations sur les modèles de code où une analyse de dépendance complète n’était pas possible. Ces avertissements sont supprimés par défaut et peuvent être activés en affectant à l’indicateur la valeur `SuppressTrimAnalysisWarnings` `false` . Pour plus d’informations sur les options de suppression disponibles, consultez [options de suppression](trimming-options.md).

> [!NOTE]
> Le découpage est une fonctionnalité expérimentale de .NET Core 3,1, 5,0, qui est _uniquement_ disponible pour les applications qui sont publiées de façon autonome.

## <a name="prevent-assemblies-from-being-trimmed"></a>Empêcher la troncation des assemblys

Il existe des scénarios dans lesquels la fonctionnalité de suppression ne parviendra pas à détecter les références. Par exemple, quand la réflexion est utilisée sur un assembly de Runtime, que ce soit par votre application ou une bibliothèque référencée par votre application, l’assembly n’est pas directement référencé. Le rognage ne tient pas compte de ces références indirectes et exclut la bibliothèque du dossier publié.

Lorsque le code référence indirectement un assembly par le biais de la réflexion, vous pouvez empêcher la troncation de l’assembly avec le `<TrimmerRootAssembly>` paramètre. L’exemple suivant montre comment empêcher la troncation d’un assembly appelé `System.Security` assembly :

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Découper votre application-CLI

Découpez votre application à l’aide de la commande [dotnet Publish](../tools/dotnet-publish.md) . Lorsque vous publiez votre application, définissez les propriétés suivantes :

- Publier en tant qu’application autonome pour un Runtime spécifique : `-r win-x64`
- Activer le découpage : `/p:PublishTrimmed=true`

L’exemple suivant publie une application pour Windows comme autonome et découpe la sortie.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

L’exemple suivant publie une application en mode de découpage agressif où le code inutilisé dans les assemblys est tronqué et les avertissements de découpage sont activés.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Découper votre application-Visual Studio

Visual Studio crée des profils de publication réutilisables qui contrôlent la façon dont votre application est publiée.

01. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le projet que vous souhaitez publier. Sélectionnez **publier...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

    Si vous ne disposez pas déjà d’un profil de publication, suivez les instructions pour en créer un et choisissez le type cible du **dossier** .

01. Choisissez **Modifier**.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Profil de publication Visual Studio avec le bouton modifier.":::

01. Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :

    - Définissez **le** **mode de déploiement** sur autonome.
    - Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.
    - Sélectionnez **découper les assemblys inutilisés (en**préversion).

    Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Boîte de dialogue Paramètres de profil avec les options mode de déploiement, Runtime cible et découper les assemblys inutilisés mis en surbrillance.":::

01. Choisissez **publier** pour publier votre application supprimée.

Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Découper votre application-Visual Studio pour Mac

Visual Studio pour Mac ne fournit pas d’options pour découper votre application pendant la publication. Vous devez publier manuellement en suivant les instructions de la section [Trim Your App-CLI](#trim-your-app---cli) . Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications .net Core](index.md).
- [Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).
- [Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).
- [commande dotnet Publish](../tools/dotnet-publish.md).
