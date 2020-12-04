---
title: Publication d’applications
description: En savoir plus sur les méthodes de publication d’une application .NET Core. .NET Core peut publier des applications spécifiques à une plateforme ou multiplateforme. Vous pouvez publier une application comme autonome ou dépendante du Framework. Chaque mode affecte la façon dont un utilisateur exécute votre application.
ms.date: 04/01/2020
ms.openlocfilehash: 03d53c8b5184d7276a69a1058d6b1b2f1e62dc81
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599575"
---
# <a name="net-core-application-publishing-overview"></a>Vue d’ensemble de la publication d’applications .NET Core

Les applications que vous créez avec .NET Core peuvent être publiées dans deux modes différents, et le mode affecte la façon dont un utilisateur exécute votre application.

La publication de votre application en tant que *contenu autonome* produit une application qui comprend le runtime et les bibliothèques .net Core, ainsi que votre application et ses dépendances. Les utilisateurs de l’application peuvent l’exécuter sur un ordinateur sur lequel le Runtime .NET Core n’est pas installé.

La publication de votre application en tant que *dépendant du Framework* produit une application qui comprend uniquement votre application et ses dépendances. Les utilisateurs de l’application doivent installer séparément le Runtime .NET Core.

Les deux modes de publication produisent un fichier exécutable propre à la plateforme par défaut. Les applications dépendantes du Framework peuvent être créées sans exécutable, et ces applications sont multiplateformes.

Quand un fichier exécutable est généré, vous pouvez spécifier la plateforme cible avec un identificateur de Runtime (RID). Pour plus d’informations sur les RID, consultez [catalogue RID .net Core](../rid-catalog.md).

Le tableau suivant présente les commandes utilisées pour publier une application comme étant dépendante de l’infrastructure ou autonome, par version du kit de développement logiciel (SDK) :

| Type                                                                                     | SDK 2.1 | SDK 3. x | Commande |
| ---------------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [exécutable dépendant du Framework](#publish-framework-dependent) pour la plateforme actuelle. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [exécutable dépendant du Framework](#publish-framework-dependent) pour une plateforme spécifique.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [binaire multiplateforme dépendant du Framework](#publish-framework-dependent).               | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [exécutable autonome](#publish-self-contained).                                    | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

Pour plus d’informations, consultez [dotnet Publish commande .net Core](../tools/dotnet-publish.md).

## <a name="produce-an-executable"></a>Produire un exécutable

Les exécutables ne sont pas multiplateformes. Elles sont spécifiques à un système d’exploitation et à une architecture de processeur. Lors de la publication de votre application et de la création d’un exécutable, vous pouvez publier l’application comme étant [autonome](#publish-self-contained) ou [dépendante](#publish-framework-dependent)de l’infrastructure. La publication d’une application comme autonome comprend le Runtime .NET Core avec l’application, et les utilisateurs de l’application n’ont pas à se soucier de l’installation de .NET Core avant d’exécuter l’application. Les applications publiées comme dépendantes du Framework n’incluent pas le runtime et les bibliothèques .NET Core ; seule l’application et les dépendances tierces sont incluses.

Les commandes suivantes produisent un exécutable :

| Type                                                                                     | SDK 2.1 | SDK 3. x | Commande |
| ---------------------------------------------------------------------------------------- | ------- | ------- | ------- |
| [exécutable dépendant du Framework](#publish-framework-dependent) pour la plateforme actuelle. |         | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |
| [exécutable dépendant du Framework](#publish-framework-dependent) pour une plateforme spécifique.  |         | ✔️      | [`dotnet publish -r <RID> --self-contained false`](../tools/dotnet-publish.md) |
| [exécutable autonome](#publish-self-contained).                                    | ✔️      | ✔️      | [`dotnet publish -r <RID>`](../tools/dotnet-publish.md) |

## <a name="produce-a-cross-platform-binary"></a>Produire un binaire multiplateforme

Les binaires multiplateforme sont créés lorsque vous publiez votre application comme étant [dépendante du Framework](#publish-framework-dependent), sous la forme d’un fichier *dll* . Le fichier *dll* est nommé d’après votre projet. Par exemple, si vous avez une application nommée **word_reader**, un fichier nommé *word_reader.dll* est créé. Les applications publiées de cette manière sont exécutées avec la `dotnet <filename.dll>` commande et peuvent être exécutées sur n’importe quelle plateforme.

Les binaires multiplateforme peuvent être exécutés sur n’importe quel système d’exploitation tant que le Runtime .NET Core ciblé est déjà installé. Si le Runtime .NET Core ciblé n’est pas installé, l’application peut s’exécuter à l’aide d’un Runtime plus récent si l’application est configurée pour effectuer une restauration par progression. Pour plus d’informations, consultez [restauration par progression des applications dépendantes du Framework](../versions/selection.md#framework-dependent-apps-roll-forward).

La commande suivante génère un binaire multiplateforme :

| Type                                                                                 | SDK 2.1 | SDK 3. x | Commande |
| -----------------------------------------------------------------------------------  | ------- | ------- | ------- |
| [binaire multiplateforme dépendant du Framework](#publish-framework-dependent).           | ✔️      | ✔️      | [`dotnet publish`](../tools/dotnet-publish.md) |

## <a name="publish-framework-dependent"></a>Publier le Framework dépendant du Framework

Les applications publiées comme dépendantes du Framework sont inter-plateformes et n’incluent pas le Runtime .NET Core. L’utilisateur de votre application est tenu d’installer le Runtime .NET Core.

La publication d’une application en tant que dépendant du Framework produit un fichier [binaire multiplateforme](#produce-a-cross-platform-binary) en tant que fichier *dll* et un [exécutable spécifique à la plateforme](#produce-an-executable) qui cible votre plateforme actuelle. La *dll* est multiplateforme, contrairement à l’exécutable. Par exemple, si vous publiez une application nommée **word_reader** et Windows cible, un exécutable *word_reader.exe* est créé avec *word_reader.dll*. Quand vous ciblez Linux ou macOS, un exécutable *word_reader* est créé avec *word_reader.dll*. Pour plus d’informations sur les RID, consultez [catalogue RID .net Core](../rid-catalog.md).

> [!IMPORTANT]
> Kit SDK .NET Core 2,1 ne génère pas d’exécutables spécifiques à la plateforme lorsque vous publiez une application qui dépend de l’infrastructure.

Le binaire multiplateforme de votre application peut être exécuté à l’aide de la `dotnet <filename.dll>` commande et peut être exécuté sur n’importe quelle plateforme. Si l’application utilise un package NuGet qui a des implémentations spécifiques à la plateforme, toutes les dépendances de plateformes sont copiées dans le dossier de publication avec l’application.

Vous pouvez créer un exécutable pour une plateforme spécifique en passant les `-r <RID> --self-contained false` paramètres à la [`dotnet publish`](../tools/dotnet-publish.md) commande. Lorsque le `-r` paramètre est omis, un fichier exécutable est créé pour votre plateforme actuelle. Tous les packages NuGet qui ont des dépendances spécifiques à la plateforme pour la plateforme ciblée sont copiés dans le dossier de publication. Si vous n’avez pas besoin d’un exécutable spécifique à Platfrom, vous pouvez spécifier `<UseAppHost>False</UseAppHost>` dans le fichier projet. Pour plus d’informations, consultez [référence MSBuild pour les projets SDK .net](../project-sdk/msbuild-props.md#useapphost).

### <a name="advantages"></a>Avantages

- **Déploiement de petite taille**\
Seule votre application et ses dépendances sont distribuées. Le runtime et les bibliothèques .NET Core sont installés par l’utilisateur et toutes les applications partagent le Runtime.

- **Multiplateforme**\
Votre application et les autres. La bibliothèque basée sur le réseau s’exécute sur d’autres systèmes d’exploitation. Vous n’avez pas besoin de définir une plateforme cible pour votre application. Pour plus d’informations sur le format de fichier .NET, consultez [format de fichier d’assembly .net](../../standard/assembly/file-format.md).

- **Utilise le dernier Runtime corrigé**\
L’application utilise le runtime le plus récent (au sein de la famille principale de .NET Core ciblée) installé sur le système cible. Cela signifie que votre application utilise automatiquement la dernière version corrigée du Runtime .NET Core. Ce comportement par défaut peut être substitué. Pour plus d’informations, consultez [restauration par progression des applications dépendantes du Framework](../versions/selection.md#framework-dependent-apps-roll-forward).

### <a name="disadvantages"></a>Inconvénients

- **Nécessite la préinstallation du Runtime**\
Votre application peut s’exécuter uniquement si la version de .NET Core ciblée par votre application est déjà installée sur le système hôte. Vous pouvez configurer le comportement de restauration par progression pour que l’application nécessite une version spécifique de .NET Core ou autorise une version plus récente de .NET Core. Pour plus d’informations, consultez [restauration par progression des applications dépendantes du Framework](../versions/selection.md#framework-dependent-apps-roll-forward).

- **.NET Core peut changer**\
Il est possible que le runtime et les bibliothèques .NET Core soient mis à jour sur l’ordinateur sur lequel l’application est exécutée. Dans de rares cas, cela peut modifier le comportement de votre application si vous utilisez les bibliothèques .NET Core, lesquelles font la plupart des applications. Vous pouvez configurer la façon dont votre application utilise les versions plus récentes de .NET Core. Pour plus d’informations, consultez [restauration par progression des applications dépendantes du Framework](../versions/selection.md#framework-dependent-apps-roll-forward).

L’inconvénient suivant s’applique uniquement au kit de développement logiciel (SDK) .NET Core 2,1.

- **Utilisez la `dotnet` commande pour démarrer l’application**\
Les utilisateurs doivent exécuter la `dotnet <filename.dll>` commande pour démarrer votre application. Le kit de développement logiciel (SDK) .NET Core 2,1 ne génère pas d’exécutables spécifiques à la plateforme pour les applications qui dépendent de l’infrastructure.

### <a name="examples"></a>Exemples

Publiez une application qui dépend de l’infrastructure multiplateforme. Un fichier exécutable qui cible votre plateforme actuelle est créé avec le fichier *dll* .

```dotnet
dotnet publish
```

Publiez une application qui dépend de l’infrastructure multiplateforme. Un fichier exécutable Linux 64 bits est créé avec le fichier *dll* . Cette commande ne fonctionne pas avec kit SDK .NET Core 2,1.

```dotnet
dotnet publish -r linux-x64 --self-contained false
```

## <a name="publish-self-contained"></a>Publication autonome

La publication de votre application en tant que contenu autonome produit un fichier exécutable spécifique à la plateforme. Le dossier de publication de sortie contient tous les composants de l’application, y compris les bibliothèques .NET Core et le runtime cible. L’application est isolée des autres applications .NET Core et n’utilise pas un runtime partagé installé localement. L’utilisateur de votre application n’est pas obligé de télécharger et d’installer .NET Core.

Le binaire exécutable est généré pour la plateforme cible spécifiée. Par exemple, si vous avez une application nommée **word_reader** et que vous publiez un exécutable autonome pour Windows, un fichier *word_reader.exe* est créé. La publication pour Linux ou macOS, un fichier de *word_reader* est créé. La plateforme et l’architecture cibles sont spécifiées avec le `-r <RID>` paramètre de la [`dotnet publish`](../tools/dotnet-publish.md) commande. Pour plus d’informations sur les RID, consultez [catalogue RID .net Core](../rid-catalog.md).

Si l’application possède des dépendances spécifiques à la plateforme, telles qu’un package NuGet contenant des dépendances spécifiques à la plateforme, celles-ci sont copiées dans le dossier de publication avec l’application.

### <a name="advantages"></a>Avantages

- **Contrôler la version de .NET Core**\
Vous contrôlez la version de .NET Core qui est déployée avec votre application.

- **Ciblage spécifique à la plateforme**\
Étant donné que vous devez publier votre application pour chaque plateforme, vous savez où votre application s’exécutera. Si .NET Core introduit une nouvelle plateforme, les utilisateurs ne peuvent pas exécuter votre application sur cette plateforme tant que vous n’avez pas publié une version ciblant cette plateforme. Vous pouvez tester votre application pour résoudre les problèmes de compatibilité avant que vos utilisateurs exécutent votre application sur la nouvelle plateforme.

### <a name="disadvantages"></a>Inconvénients

- **Déploiements plus importants**\
Étant donné que votre application comprend le Runtime .NET Core et toutes les dépendances de votre application, la taille du téléchargement et l’espace disque requis sont supérieurs à ceux d’une version [dépendante du Framework](#publish-framework-dependent) .

  > [!TIP]
  > Vous pouvez réduire la taille de votre déploiement sur les systèmes Linux d’environ 28 Mo en utilisant le [*mode de globalisation de la globalisation*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).net core. Cela force votre application à traiter toutes les cultures comme la [culture dite indifférente](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

  > [!TIP]
  > Il existe une [fonctionnalité de découpage](trim-self-contained.md) de la version préliminaire qui peut réduire encore davantage la taille de votre déploiement.

- **Plus difficile à mettre à jour la version .NET Core**\
Le Runtime .NET Core (distribué avec votre application) peut uniquement être mis à niveau en publiant une nouvelle version de votre application. Toutefois, .NET Core met à jour les correctifs de sécurité critiques en fonction des besoins de la bibliothèque d’infrastructure sur l’ordinateur sur lequel votre application s’exécute. Vous êtes responsable de la validation de bout en bout pour ce scénario de correctif de sécurité.

### <a name="examples"></a>Exemples

Publiez une application autonome. Un fichier exécutable macOS 64 bits est créé.

```dotnet
dotnet publish -r osx-x64
```

Publiez une application autonome. Un fichier exécutable Windows 64 bits est créé.

```dotnet
dotnet publish -r win-x64
```

## <a name="publish-with-readytorun-images"></a>Publier avec des images ReadyToRun

La publication avec des images ReadyToRun améliore le temps de démarrage de votre application au prix de l’augmentation de la taille de votre application. Pour publier avec ReadyToRun, consultez [ReadyToRun](ready-to-run.md) pour plus d’informations.

### <a name="advantages"></a>Avantages

- **Amélioration du temps de démarrage**\
L’application passera moins de temps à exécuter le JIT.

### <a name="disadvantages"></a>Inconvénients

- **Taille supérieure**\
L’application sera plus volumineuse sur le disque.

### <a name="examples"></a>Exemples

Publiez une application autonome et ReadyToRun. Un fichier exécutable macOS 64 bits est créé.

```dotnet
dotnet publish -c Release -r osx-x64 -p:PublishReadyToRun=true
```

Publiez une application autonome et ReadyToRun. Un fichier exécutable Windows 64 bits est créé.

```dotnet
dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
```

## <a name="see-also"></a>Voir aussi

- [Déploiement d’applications .NET Core avec CLI .NET Core.](deploy-with-cli.md)
- [Déploiement d’applications .NET Core avec Visual Studio.](deploy-with-vs.md)
- [Catalogue d’identificateurs de Runtime (RID) .NET Core.](../rid-catalog.md)
- [Sélectionnez la version de .NET Core à utiliser.](../versions/selection.md)
