---
title: Vue d’ensemble de global.json
description: Découvrez comment utiliser le fichier global.json pour définir la version du kit SDK .NET Core pendant l’exécution de commandes CLI .NET Core.
ms.date: 12/03/2018
ms.custom: updateeachrelease, seodec18
ms.openlocfilehash: 2c1fec102993b61e1eb699e8d3508b773302f569
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117431"
---
# <a name="globaljson-overview"></a>Vue d’ensemble de global.json

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

Le fichier *global.json* vous permet de définir la version du kit SDK .NET Core utilisée pendant l’exécution des commandes de l’interface CLI .NET Core. La sélection du kit SDK .NET Core est indépendante de la spécification du runtime ciblé par votre projet. La version du kit SDK .NET Core détermine les versions des outils CLI .NET Core qui sont utilisées. En règle générale, il est préférable d’utiliser la dernière version des outils. Dans ce cas, aucun fichier *global.json* n’est nécessaire.

Pour plus d’informations sur la spécification du runtime, consultez [Versions cibles de .NET Framework](../../standard/frameworks.md).

Le kit SDK .NET Core recherche un fichier *global.json* dans le répertoire de travail actif (qui n’est pas nécessairement le même que le répertoire du projet) ou dans l’un de ses répertoires parents.

## <a name="globaljson-schema"></a>Schéma de global.json

### <a name="sdk"></a>sdk

Type : Object

Spécifie des informations sur le kit SDK .NET Core à sélectionner.

#### <a name="version"></a>version

Type : Chaîne

Version du kit SDK .NET Core à utiliser.

Notez que ce champ :

- Ne prend pas en charge l’utilisation de caractères génériques. Autrement dit, il convient de spécifier le numéro complet de la version.
- Ne prend pas en charge les plages de versions.

L’exemple suivant montre le contenu d’un fichier *global.json* :

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.JSON et l’interface CLI .NET Core

Il est utile de connaître les versions disponibles pour en définir une dans le fichier *global.json*. Vous trouverez la liste complète des kits de développement logiciel (SDK) disponibles pris en charge sur la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) . À partir du kit SDK .NET Core 2.1, vous pouvez exécuter la commande suivante pour savoir quelles versions du kit SDK sont déjà installées sur votre ordinateur :

```dotnetcli
dotnet --list-sdks
```

Pour installer des versions de kit SDK .NET Core supplémentaires sur votre ordinateur, visitez la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .

Vous pouvez créer un fichier *global.json* dans le répertoire actif en exécutant la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :

```dotnetcli
dotnet new globaljson --sdk-version 2.2.100
```

## <a name="matching-rules"></a>Règles de correspondance

> [!NOTE]
> Les règles de correspondance sont régies par apphost, qui fait partie du runtime .NET Core.
> La dernière version de l’hôte est utilisée quand plusieurs runtimes sont installés côte à côte.

À partir de .NET Core 2.0, voici les règles qui s’appliquent pour déterminer quelle version du kit SDK utiliser :

- Si aucun fichier *global.json* n’est trouvé ou que *global.json* ne spécifie pas de version du kit SDK, la dernière version installée du kit SDK est utilisée. La dernière version du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte).
- Si la version du kit SDK n’est pas spécifiée dans *global.json* :
  - Si la version spécifiée du kit SDK se trouve sur la machine, c’est cette même version qui est utilisée.
  - Si la version spécifiée du kit SDK est introuvable sur la machine, c’est la dernière **version corrective** installée du kit SDK qui est utilisée. La dernière **version corrective** installée du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte). Dans .NET Core 2.1 et ultérieur, les **versions correctives** antérieures à la **version corrective** spécifiée sont ignorées dans la sélection du kit SDK.
  - Dans le cas où ni la version spécifiée du kit SDK, ni une **version corrective** appropriée du kit SDK n’est trouvée, une erreur est générée.

La version du kit SDK se compose actuellement des éléments suivants :

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

La **future version** du kit SDK .NET Core est représentée par le premier chiffre (`x`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. En règle générale, le cycle de lancement du kit SDK .NET Core est plus rapide que celui de .NET Core.

La **version corrective** est définie par les deux derniers chiffres (`yz`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. Par exemple, si vous spécifiez la version `2.1.300` du kit SDK, le mécanisme de sélection du kit SDK trouve la version `2.1.399`, mais la version `2.1.400` n’est pas considérée comme une version corrective de la version `2.1.300`.

Les versions du kit SDK .NET Core comprises entre `2.1.100` et `2.1.201` ont été lancées pendant la période transitoire entre les modèles de numérotation des versions et ne gèrent pas correctement la notation `xyz`. Si vous spécifiez ces versions dans le fichier *global.json*, nous vous recommandons vivement de vérifier que les versions spécifiées se trouvent sur les machines cibles.

Pour le kit SDK .NET Core 1.x, si vous avez spécifié une version et qu’aucune correspondance exacte n’a été trouvée, la dernière version installée du kit SDK a été utilisée. La dernière version du kit SDK peut être une version ou une préversion (le numéro de version le plus élevé l’emporte).

## <a name="troubleshooting-build-warnings"></a>Résolutions des problèmes liés aux avertissements de build

> [!WARNING]
> Vous utilisez une préversion du kit SDK .NET Core. Vous pouvez définir la version du kit SDK via un fichier global.json dans le projet actif. Pour plus d’informations, consultez <https://go.microsoft.com/fwlink/?linkid=869452>

Cet avertissement indique que votre projet est compilé à partir d’une préversion du kit SDK .NET Core, comme indiqué dans la section [Règles de correspondance](#matching-rules). Les versions du kit SDK .NET Core jouissent d’une image et d’un engagement de qualité. Cependant, si vous ne voulez pas utiliser de préversion, ajoutez un fichier *global.json* à la structure hiérarchique de votre projet pour spécifier la version du kit SDK à utiliser, puis utilisez `dotnet --list-sdks` pour vérifier que la version est installée sur votre machine. Pour utiliser une nouvelle version au moment où celle-ci est lancée, supprimez le fichier *global.json* ou mettez-le à jour pour utiliser la version plus récente.

> [!WARNING]
> Le projet de démarrage '{startupProject}' cible le framework '.NETCoreApp' version '{targetFrameworkVersion}'. Cette version des outils en ligne de commande Entity Framework Core .NET prend uniquement en charge la version 2.0 ou supérieure. Pour plus d’informations sur l’utilisation d’anciennes versions des outils, consultez <https://go.microsoft.com/fwlink/?linkid=871254>.

À partir du kit SDK .NET Core 2.1 (version 2.1.300), la commande `dotnet ef` est incluse dans le kit SDK. Cet avertissement indique que votre projet cible EF Core 1.0 ou 1.1, qui n’est pas compatible avec le kit SDK .NET Core 2.1 (et les versions ultérieures). Pour compiler votre projet, installez le kit SDK .NET Core 2.0 (version 2.1.201) ou une version antérieure sur votre ordinateur et définissez la version du SDK à utiliser dans le fichier *global.json*. Pour plus d’informations sur la commande `dotnet ef`, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Voir aussi

- [Méthode de résolution des kits SDK de projet](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
