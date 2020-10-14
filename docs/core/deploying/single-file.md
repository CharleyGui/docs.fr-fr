---
title: Application à fichier unique
description: Découvrez ce qu’est une application à fichier unique et pourquoi envisager d’utiliser ce modèle de déploiement d’application.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 16e9586cfc29072fa2ca70dc482272a5a0e7306a
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050414"
---
# <a name="single-file-deployment-and-executable"></a>Déploiement et exécutable d’un seul fichier

L’empaquetage de tous les fichiers dépendants de l’application dans un seul fichier binaire fournit à un développeur d’applications l’option intéressante pour déployer et distribuer l’application en tant que fichier unique. Ce modèle de déploiement est disponible depuis .NET Core 3,0 et a été amélioré dans .NET 5,0. Précédemment dans .NET Core 3,0, lorsqu’un utilisateur exécute votre application à fichier unique, l’hôte .NET Core extrait d’abord tous les fichiers dans un répertoire temporaire avant d’exécuter l’application. .NET 5,0 améliore cette expérience en exécutant directement le code sans avoir besoin d’extraire les fichiers de l’application.

Le déploiement d’un seul fichier est disponible pour le [modèle de déploiement dépendant du Framework](index.md#publish-framework-dependent) et pour les [applications autonomes](index.md#publish-self-contained). La taille du fichier unique dans une application autonome est importante, car elle inclut le runtime et les bibliothèques de Framework. L’option de déploiement de fichier unique peut être combinée avec [ReadyToRun](ready-to-run.md) et [Trim (une fonctionnalité expérimentale dans .net 5,0) options de](trim-self-contained.md) publication.

## <a name="api-incompatibility"></a>Incompatibilité d’API

Certaines API ne sont pas compatibles avec le déploiement à fichier unique et les applications peuvent nécessiter une modification si elles utilisent ces API. Si vous utilisez un Framework ou un package tiers, il est possible qu’ils puissent également utiliser l’une de ces API et qu’il soit nécessaire de les modifier. La cause la plus courante de problèmes dépend des chemins d’accès aux fichiers ou dll livrés avec l’application.

Le tableau ci-dessous contient les détails de l’API de la bibliothèque Runtime appropriée pour une utilisation à fichier unique.

| API                            | Notes                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | Retourne une chaîne vide.                                               |
| `Module.FullyQualifiedName`    | Retourne une chaîne avec la valeur de `<Unknown>` ou lève une exception. |
| `Module.Name`                  | Retourne une chaîne avec la valeur de `<Unknown>` .                        |
| `Assembly.GetFile`             | Lève <xref:System.IO.IOException>.                                   |
| `Assembly.GetFiles`            | Lève <xref:System.IO.IOException>.                                   |
| `Assembly.CodeBase`            | Lève <xref:System.PlatformNotSupportedException>.                    |
| `Assembly.EscapedCodeBase`     | Lève <xref:System.PlatformNotSupportedException>.                    |
| `AssemblyName.CodeBase`        | Retourne `null`.                                                        |
| `AssemblyName.EscapedCodeBase` | Retourne `null`.                                                        |

Nous avons des recommandations pour la résolution des scénarios courants :

* Pour accéder aux fichiers à côté de l’exécutable, utilisez <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> .

* Pour rechercher le nom de fichier de l’exécutable, utilisez le premier élément de <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> .

* Pour éviter d’expédier entièrement des fichiers libres, envisagez d’utiliser des [ressources incorporées](../../framework/resources/creating-resource-files-for-desktop-apps.md).

## <a name="attaching-a-debugger"></a>Attachement d’un débogueur

Sur Linux, le seul débogueur pouvant être attaché à des processus de fichier unique autonomes ou à des vidages sur incident de débogage est [SOS avec LLDB](../diagnostics/dotnet-sos.md).

Sur Windows et Mac, Visual Studio et VS Code peuvent être utilisés pour déboguer des vidages sur incident. L’attachement à un exécutable autonome à fichier unique en cours d’exécution requiert un fichier supplémentaire : _mscordbi. { dll, so}_.

Sans ce fichier, Visual Studio peut générer l’erreur «Impossible d’attacher au processus. Un composant de débogage n’est pas installé.» et VS Code peut générer l’erreur « Échec de l’attachement au processus : erreur inconnue : 0x80131c3c ».

Pour corriger ces erreurs, _mscordbi_ doit être copié en regard de l’exécutable. _mscordbi_ est `publish` Ed par défaut dans le sous-répertoire avec l’ID d’exécution de l’application. Ainsi, par exemple, s’il s’agit de publier un fichier exécutable à fichier unique autonome à l’aide `dotnet` de l’interface CLI pour Windows à l’aide des paramètres `-r win-x64` , l’exécutable est placé dans _bin/debug/net 5.0/Win-x64/Publish_. Une copie de _mscordbi.dll_ serait présente dans _bin/debug/net 5.0/Win-x64_.

## <a name="other-considerations"></a>Autres considérations

Un fichier unique ne regroupe pas les bibliothèques natives par défaut. Sur Linux, nous prévoyons le runtime dans le bundle et seules les bibliothèques natives de l’application sont déployées dans le même répertoire que l’application à fichier unique. Sur Windows, nous prévoyons uniquement le code d’hébergement et les bibliothèques Runtime et application natives sont déployées dans le même répertoire que l’application à fichier unique. Cela permet de garantir une bonne expérience de débogage, qui requiert que les fichiers natifs soient exclus du fichier unique. Il existe une option pour définir un indicateur, `IncludeNativeLibrariesForSelfExtract` , pour inclure les bibliothèques natives dans le groupe de fichiers unique, mais ces fichiers seront extraits dans un répertoire temporaire de l’ordinateur client lors de l’exécution de l’application à fichier unique.

Une application à fichier unique aura tous les fichiers PDB associés et ne sera pas regroupée par défaut. Si vous souhaitez inclure des fichiers PDB à l’intérieur de l’assembly pour les projets que vous générez, affectez la valeur `DebugType` `embedded` décrite [ci-dessous](#include-pdb-files-inside-the-bundle) en détail.

Les composants C++ managés ne sont pas adaptés au déploiement à fichier unique et nous vous recommandons d’écrire des applications en C# ou un autre langage C++ non managé pour qu’ils soient compatibles avec un seul fichier.

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

## <a name="include-pdb-files-inside-the-bundle"></a>Inclure des fichiers PDB dans le bundle

Le fichier PDB d’un assembly peut être incorporé dans l’assembly lui-même (le `.dll` ) à l’aide du paramètre ci-dessous. Étant donné que les symboles font partie de l’assembly, ils feront également partie de l’application à fichier unique :

```xml
<DebugType>embedded</DebugType>
```

Par exemple, ajoutez la propriété suivante au fichier projet d’un assembly pour incorporer le fichier PDB à cet assembly :

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
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

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

01. Dans la boîte de dialogue **paramètres de profil** , définissez les options suivantes :

    - Définissez **le** **mode de déploiement** sur autonome.
    - Définissez le **Runtime cible** sur la plateforme sur laquelle vous souhaitez publier.
    - Sélectionnez **produire un fichier unique**.

    Choisissez **Enregistrer** pour enregistrer les paramètres et revenir à la boîte de dialogue **publier** .

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Explorateur de solutions avec un menu contextuel, sélectionnez l’option publier.":::

01. Choisissez **publier** pour publier votre application en tant que fichier unique.

Pour plus d’informations, consultez [publier des applications .net core avec Visual Studio](deploy-with-vs.md).

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a>Publier une application à fichier unique-Visual Studio pour Mac

Visual Studio pour Mac ne fournit pas d’options permettant de publier votre application sous la forme d’un fichier unique. Vous devez publier manuellement en suivant les instructions de la section [publication d’une application à fichier unique-CLI](#publish-a-single-file-app---cli) . Pour plus d’informations, consultez [publier des applications .net core avec CLI .net Core](deploy-with-cli.md).

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications .net Core](index.md).
- [Publiez des applications .net core avec CLI .net Core](deploy-with-cli.md).
- [Publiez des applications .net core avec Visual Studio](deploy-with-vs.md).
- [ `dotnet publish` commande](../tools/dotnet-publish.md).
