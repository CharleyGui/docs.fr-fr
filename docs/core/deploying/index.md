---
title: Publication d’applications
description: Découvrez les façons de publier une application .NET Core. .NET Core peut publier des applications spécifiques à la plate-forme ou multiplateformes. Vous pouvez publier une application en tant qu’autonome ou en tant que dépendante de l’exécution. Chaque mode affecte la façon dont un utilisateur exécute votre application.
ms.date: 04/01/2020
ms.openlocfilehash: a4e5f9fe048d40c751f582bd49732cb903202db4
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665536"
---
# <a name="net-core-application-publishing-overview"></a>.NET Aperçu de publication d’applications de base

Les applications que vous créez avec .NET Core peuvent être publiées en deux modes différents, et le mode affecte la façon dont un utilisateur exécute votre application.

La publication de votre application en tant *qu’autonome* produit une application qui inclut le temps d’exécution et les bibliothèques .NET Core, ainsi que votre application et ses dépendances. Les utilisateurs de l’application peuvent l’exécuter sur une machine qui n’a pas le temps d’exécution .NET Core installé.

La publication de votre application en tant que *dépendante du temps d’exécution* (précédemment connue sous le nom *de cadre-dépendante)* produit une application qui ne comprend que votre application elle-même et ses dépendances. Les utilisateurs de l’application doivent installer séparément le temps d’exécution .NET Core.

Les deux modes de publication produisent une plate-forme spécifique exécutable par défaut. Les applications dépendantes de l’exécution peuvent être créées sans exécutable, et ces applications sont multiplateformes.

Lorsqu’un exécutable est produit, vous pouvez spécifier la plate-forme cible avec un identifiant de temps d’exécution (RID). Pour plus d’informations sur les RID, voir [.NET Core RID Catalog](../rid-catalog.md).

Le tableau suivant décrit les commandes utilisées pour publier une application en tant que dépendante de l’exécution ou autonome, par version SDK :

| Type                                                                                 | SDK 2.1 | SDK 3.x | Commande |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [exécutable pour la plate-forme](#publish-runtime-dependent) actuelle. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [exécutable pour une plate-forme](#publish-runtime-dependent) spécifique.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [runtime-dépendant transversal binaire](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [autonomes exécutables](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Pour plus d’informations, voir [.NET Core dotnet publier la commande](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Produire un exécutable

Les exécutions ne sont pas multiplateformes. Ils sont spécifiques à un système d’exploitation et l’architecture CPU. Lors de la publication de votre application et de la création d’un exécutable, vous pouvez publier l’application en tant que [autonome](#publish-self-contained) ou [dépendante de l’exécution](#publish-runtime-dependent). La publication d’une application en tant qu’autonome inclut l’heure d’exécution .NET Core avec l’application, et les utilisateurs de l’application n’ont pas à se soucier de l’installation de .NET Core avant d’exécuter l’application. Les applications publiées sous le titre runtime-dependent ne comprennent pas le temps d’exécution et les bibliothèques .NET Core; seules les dépendances de l’application et de la 3e partie sont incluses.

Les commandes suivantes produisent un exécutable :

| Type                                                                                 | SDK 2.1 | SDK 3.x | Commande |
| ------------------------------------------------------------------------------------ | ------- | ------- | ------- |
| [exécutable pour la plate-forme](#publish-runtime-dependent) actuelle. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [exécutable pour une plate-forme](#publish-runtime-dependent) spécifique.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [autonomes exécutables](#publish-self-contained).                                | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Produire un binaire multiplateforme

Les binaires multiplateformes sont créés lorsque vous publiez votre application en tant que dépendante de [l’exécution,](#publish-runtime-dependent)sous la forme *d’un fichier dll.* Le fichier *dll* est nommé d’après votre projet. Par exemple, si vous avez une application nommée **word_reader**, un fichier nommé *word_reader.dll* est créé. Les applications publiées de cette `dotnet <filename.dll>` manière sont exécutées avec la commande et peuvent être exécutées sur n’importe quelle plate-forme.

Les binaires multiplateformes peuvent être exécutés sur n’importe quel système d’exploitation tant que le temps d’exécution .NET Core ciblé est déjà installé. Si le temps d’exécution .NET Core ciblé n’est pas installé, l’application peut s’exécuter à l’aide d’un temps d’exécution plus récent si l’application est configurée pour rouler vers l’avant. Pour plus d’informations, voir [les applications dépendantes de l’exécution rouler vers l’avant](../versions/selection.md#framework-dependent-apps-roll-forward).

La commande suivante produit un binaire multiplateforme :

| Type                                                                                 | SDK 2.1 | SDK 3.x | Commande |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [runtime-dépendant transversal binaire](#publish-runtime-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-runtime-dependent"></a>Publier runtime-dependent

Les applications publiées en tant que dépendantes du temps d’exécution sont multiplateformes et n’incluent pas le temps d’exécution .NET Core. L’utilisateur de votre application est tenu d’installer le temps d’exécution .NET Core.

La publication d’une application dépendante du temps d’exécution produit un [binaire multiplateforme](#produce-a-cross-platform-binary) comme un fichier *dll,* et une [plate-forme spécifique exécutable](#produce-an-executable) qui cible votre plate-forme actuelle. Le *dll* est multi-plateforme tandis que l’exécuteur ne l’est pas. Par exemple, si vous publiez une application nommée **word_reader** et ciblez Windows, un *word_reader.exe exe exe exable* est créé avec *word_reader.dll*. Lors du ciblage Linux ou macOS, un *word_reader* exécutable est créé avec *word_reader.dll*. Pour plus d’informations sur les RID, voir [.NET Core RID Catalog](../rid-catalog.md).

> [!IMPORTANT]
> .NET Core SDK 2.1 ne produit pas d’exécutables spécifiques à la plate-forme lorsque vous publiez une application dépendante du temps d’exécution.

Le binaire multiplateforme de votre `dotnet <filename.dll>` application peut être exécuté avec la commande, et peut être exécuté sur n’importe quelle plate-forme. Si l’application utilise un package NuGet qui dispose d’implémentations spécifiques à la plate-forme, les dépendances de toutes les plates-formes sont copiées sur le dossier de publication avec l’application.

Vous pouvez créer un exécutable `-r <RID> --self-contained false` pour une [`dotnet publish`](../tools/dotnet-publish.md) plate-forme spécifique en passant les paramètres à la commande. Lorsque `-r` le paramètre est omis, un exécutant est créé pour votre plate-forme actuelle. Tous les paquets NuGet qui ont des dépendances spécifiques à la plate-forme pour la plate-forme ciblée sont copiés sur le dossier de publication.

### <a name="advantages"></a>Avantages

- **Petit déploiement**\
Seule votre application et ses dépendances sont distribuées. Le temps d’exécution .NET Core et les bibliothèques sont installés par l’utilisateur et toutes les applications partagent le temps d’exécution.

- **Plateforme croisée**\
Votre application et tout . La bibliothèque basée sur NET fonctionne sur d’autres systèmes d’exploitation. Vous n’avez pas besoin de définir une plate-forme cible pour votre application. Pour plus d’informations sur le format de fichier .NET, voir [.NET Assembly File Format](../../standard/assembly/file-format.md).

- **Utilise le dernier temps d’exécution patché**\
L’application utilise le dernier runtime (au sein de la famille ciblée major-mineur de .NET Core) installé sur le système cible. Cela signifie que votre application utilise automatiquement la dernière version patchée de l’exécution .NET Core. Ce comportement par défaut peut être remplacé. Pour plus d’informations, voir [les applications dépendantes de l’exécution rouler vers l’avant](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Inconvénients

- **Nécessite la pré-installation du temps d’exécution**\
Votre application ne peut s’exécuter que si la version de .NET Core vos cibles d’application est déjà installée sur le système hôte. Vous pouvez configurer le comportement roll-forward pour l’application soit pour exiger une version spécifique de .NET Core ou permettre une version plus récente de .NET Core. Pour plus d’informations, voir [les applications dépendantes de l’exécution rouler vers l’avant](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core peut changer**\
Il est possible que le temps d’exécution .NET Core et les bibliothèques soient mis à jour sur la machine où l’application est exécutée. Dans de rares cas, cela peut changer le comportement de votre application si vous utilisez les bibliothèques .NET Core, ce que la plupart des applications font. Vous pouvez configurer la façon dont votre application utilise de nouvelles versions de .NET Core. Pour plus d’informations, voir [les applications dépendantes de l’exécution rouler vers l’avant](../versions/selection.md#framework-dependent-apps-roll-forward).

Le désavantage suivant ne s’applique qu’à .NET Core 2.1 SDK.

- **Utilisez `dotnet` la commande pour démarrer l’application**\
Les utilisateurs `dotnet <filename.dll>` doivent exécuter la commande pour démarrer votre application. .NET Core 2.1 SDK ne produit pas d’exécutables spécifiques à la plate-forme pour les applications publiées dépendantes de l’exécution.

### <a name="examples"></a>Exemples

Publiez une application multi-plateforme dépendante de l’exécution. Un exécutable qui cible votre plate-forme actuelle est créé avec le fichier *dll.*

```dotnet
dotnet publish
```

Publiez une application multi-plateforme dépendante de l’exécution. Un Linux 64 bits exécutable est créé avec le fichier *dll.* Cette commande ne fonctionne pas avec .NET Core SDK 2.1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publier des contenus autonomes

La publication de votre application en tant que contenu autonome produit une plate-forme spécifique exécutable. Le dossier de publication de sortie contient tous les composants de l’application, y compris les bibliothèques .NET Core et le temps d’exécution cible. L’application est isolée des autres applications .NET Core et n’utilise pas un temps d’exécution partagé installé localement. L’utilisateur de votre application n’est pas tenu de télécharger et d’installer .NET Core.

Le binaire exécutable est produit pour la plate-forme cible spécifiée. Par exemple, si vous avez une application nommée **word_reader**, et que vous publiez un fichier autonome exécutable pour Windows, un fichier *word_reader.exe* est créé. Publication pour Linux ou macOS, un fichier *word_reader* est créé. La plate-forme et l’architecture cibles sont spécifiées avec le `-r <RID>` paramètre de la [`dotnet publish`](../tools/dotnet-publish.md) commande. Pour plus d’informations sur les RID, voir [.NET Core RID Catalog](../rid-catalog.md).

Si l’application a des dépendances spécifiques à la plate-forme, comme un paquet NuGet contenant des dépendances spécifiques à la plate-forme, celles-ci sont copiées sur le dossier de publication avec l’application.

### <a name="advantages"></a>Avantages

- **Contrôle .NET Version Core**\
Vous contrôlez la version de .NET Core qui est déployée avec votre application.

- **Ciblage spécifique à la plate-forme**\
Parce que vous devez publier votre application pour chaque plate-forme, vous savez où votre application s’exécutera. Si .NET Core introduit une nouvelle plate-forme, les utilisateurs ne peuvent pas exécuter votre application sur cette plate-forme jusqu’à ce que vous libériez une version ciblant cette plate-forme. Vous pouvez tester votre application pour des problèmes de compatibilité avant que vos utilisateurs exécutent votre application sur la nouvelle plate-forme.

### <a name="disadvantages"></a>Inconvénients

- **Déploiements plus importants**\
Étant donné que votre application comprend le temps d’exécution .NET Core et toutes vos dépendances d’application, la taille du téléchargement et l’espace de disque dur requis est supérieure à une version [dépendante du temps d’exécution.](#publish-runtime-dependent)

  > [!TIP]
  > Vous pouvez réduire la taille de votre déploiement sur les systèmes Linux d’environ 28 Mo en utilisant le [*mode invariant*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)de mondialisation .NET Core . Cela oblige votre application à traiter toutes les cultures comme la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- **Plus difficile de mettre à jour la version .NET Core**\
.NET Core Runtime (distribué avec votre application) ne peut être mis à niveau en libérant une nouvelle version de votre application. Vous êtes responsable de la fourniture d’une version mise à jour de votre application pour les correctifs de sécurité à la .NET Core Runtime.

### <a name="examples"></a>Exemples

Publier une application autonome. Un macOS 64 bits exécutable est créé.

```dotnet
dotnet publish -r osx-x64
```

Publier une application autonome. Un Windows 64 bits exécutable est créé.

```dotnet
dotnet publish -r win-x64
```

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications de base .NET avec CLI Core .NET.](deploy-with-cli.md)
- [Déploiement d’applications de base .NET avec Visual Studio.](deploy-with-vs.md)
- [Forfaits, métapackages et cadres.](../packages.md)
- [catalogue .NET Core Runtime IDentifier (RID).](../rid-catalog.md)
- [Sélectionnez la version .NET Core à utiliser.](../versions/selection.md)
