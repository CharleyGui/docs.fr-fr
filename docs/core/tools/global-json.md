---
title: Vue d’ensemble de global.json
description: Découvrez comment utiliser le fichier global.json pour définir la version du kit SDK .NET Core pendant l’exécution de commandes CLI .NET Core.
ms.date: 01/14/2020
ms.custom: updateeachrelease
ms.openlocfilehash: fedfe168e2c1a0555c2d4499ba02d270033e0d1a
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115794"
---
# <a name="globaljson-overview"></a>Vue d’ensemble de global.json

**Cet article s’applique à : ✓** .net Core 2,0 SDK et versions ultérieures

Le fichier *global.json* vous permet de définir la version du kit SDK .NET Core utilisée pendant l’exécution des commandes de l’interface CLI .NET Core. La sélection du kit SDK .NET Core est indépendante de la spécification du runtime ciblé par votre projet. La version du kit SDK .NET Core détermine les versions des outils CLI .NET Core qui sont utilisées. 

En général, vous souhaitez utiliser la version la plus récente des outils du kit de développement logiciel (SDK). aucun fichier *global. JSON* n’est donc nécessaire. Dans certains scénarios avancés, vous souhaiterez peut-être contrôler la version des outils du kit de développement logiciel (SDK), et cet article explique comment procéder.

Pour plus d’informations sur la spécification du runtime, consultez [Versions cibles de .NET Framework](../../standard/frameworks.md).

Le kit SDK .NET Core recherche un fichier *global.json* dans le répertoire de travail actif (qui n’est pas nécessairement le même que le répertoire du projet) ou dans l’un de ses répertoires parents.

## <a name="globaljson-schema"></a>Schéma de global.json

### <a name="sdk"></a>sdk

Type : `object`

Spécifie des informations sur le kit SDK .NET Core à sélectionner.

#### <a name="version"></a>Version de

- Type : `string`

- Disponible depuis : .NET Core 1,0 SDK.

Version du kit SDK .NET Core à utiliser.

Ce champ :

- Ne prend pas en charge les caractères génériques, autrement dit, le numéro de version complet doit être spécifié.
- Ne prend pas en charge les plages de versions.

#### <a name="allowprerelease"></a>allowPrerelease

- Type : `boolean`

- Disponible depuis : .NET Core 3,0 SDK.

Indique si le programme de résolution du SDK doit prendre en compte les versions préliminaires lors de la sélection de la version du kit de développement logiciel à utiliser.

Si vous ne définissez pas cette valeur explicitement, la valeur par défaut varie selon que vous exécutez à partir de Visual Studio :

- Si vous **n’êtes pas** dans Visual Studio, la valeur par défaut est `true`.
- Si vous êtes dans Visual Studio, il utilise l’état de préversion demandé. Autrement dit, si vous utilisez une préversion de Visual Studio ou que vous définissez l’option **utiliser des aperçus de l’kit SDK .net Core** ( **sous outils** > **options** > **environnement** > **fonctionnalités**en préversion), la valeur par défaut est `true`; Sinon, `false`.

#### <a name="rollforward"></a>Restauration par progression

- Type : `string`

- Disponible depuis : .NET Core 3,0 SDK.

Stratégie de restauration par progression à utiliser lors de la sélection d’une version du kit de développement logiciel (SDK) en tant que solution de secours quand une version spécifique du kit de développement logiciel est manquante ou en tant que directive pour utiliser une version plus récente. Une [version](#version) doit être spécifiée avec une valeur `rollForward`, sauf si vous la définissez sur `latestMajor`. 

Pour comprendre les stratégies disponibles et leur comportement, prenez en compte les définitions suivantes pour une version du kit de développement logiciel (SDK) au format `x.y.znn`:

- `x` est la version principale.
- `y` est la version mineure.
- `z` est la gamme de fonctionnalités.
- `nn` est la version du correctif.

Le tableau suivant indique les valeurs possibles pour la clé de `rollForward` :

| Value         | Comportement |
| ------------- | ---------- |
| `patch`       | Utilise la version spécifiée. <br> S’il est introuvable, restaure le niveau de correctif le plus récent. <br> S’il est introuvable, échoue. <br><br> Cette valeur est le comportement hérité des versions antérieures du kit de développement logiciel (SDK). |
| `feature`     | Utilise le niveau de correctif le plus récent pour la plage de fonctionnalités, mineure et principale spécifiée. <br> S’il est introuvable, restaure la bande de fonctionnalités supérieure suivante au sein du même niveau principal/secondaire et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, échoue. |
| `minor`       | Utilise le niveau de correctif le plus récent pour la plage de fonctionnalités, mineure et principale spécifiée. <br> S’il est introuvable, restaure la bande de fonctionnalités supérieure suivante au sein de la même version majeure/mineure et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, restaure par progression jusqu’à la bande de fonctionnalités et mineure supérieure suivante au sein du même principal et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, échoue. |
| `major`       | Utilise le niveau de correctif le plus récent pour la plage de fonctionnalités, mineure et principale spécifiée. <br> S’il est introuvable, restaure la bande de fonctionnalités supérieure suivante au sein de la même version majeure/mineure et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, restaure par progression jusqu’à la bande de fonctionnalités et mineure supérieure suivante au sein du même principal et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, restaure les versions ultérieures principales, secondaires et de fonctionnalités suivantes et utilise le niveau de correctif le plus récent pour cette bande de fonctionnalités. <br> S’il est introuvable, échoue. |
| `latestPatch` | Utilise le dernier niveau de correctif installé qui correspond à la bande principale, mineure et de fonctionnalité demandée avec un niveau de correctif et qui est supérieur ou égal à la valeur spécifiée. <br> S’il est introuvable, échoue. |
| `latestFeature` | Utilise la bande de fonctionnalités et le niveau de correctifs les plus élevés qui correspondent aux principaux et mineurs demandés avec une plage de fonctionnalités supérieure ou égale à la valeur spécifiée. <br> S’il est introuvable, échoue. |
| `latestMinor` | Utilise le niveau le plus élevé, la bande de fonctionnalités et le niveau de correctif logiciel qui correspond à la valeur principale demandée, avec une valeur mineure supérieure ou égale à la valeur spécifiée. <br> S’il est introuvable, échoue. |
| `latestMajor` | Utilise le kit SDK .NET Core installé le plus élevé avec une valeur Major supérieure ou égale à la valeur spécifiée. <br> S’il est introuvable, échec. |
| `disable`     | Ne restaure pas par progression. Correspondance exacte requise. |

## <a name="examples"></a>Exemples

L’exemple suivant montre comment ne pas utiliser les versions préliminaires :

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

L’exemple suivant montre comment utiliser la version la plus récente installée qui est supérieure ou égale à la version spécifiée :

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

L’exemple suivant montre comment utiliser la version spécifiée exacte :

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

L’exemple suivant montre comment utiliser la version de correctif la plus élevée installée pour une version spécifique (sous la forme 3.1.1 XX) :

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.JSON et l’interface CLI .NET Core

Il est utile de savoir quelles versions du kit de développement logiciel (SDK) sont installées sur votre ordinateur pour en définir un dans le fichier *global. JSON* . Pour plus d’informations sur la façon de procéder, consultez [Comment vérifier que .net Core est déjà installé](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Pour installer des versions de kit SDK .NET Core supplémentaires sur votre ordinateur, visitez la page [Télécharger .net Core](https://dotnet.microsoft.com/download/dotnet-core) .

Vous pouvez créer un fichier *global.json* dans le répertoire actif en exécutant la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Règles de correspondance

> [!NOTE]
> Les règles de correspondance sont régies par le point d’entrée `dotnet.exe`, qui est courant pour tous les runtimes installés .NET Core installés. Les règles de correspondance pour la dernière version installée du Runtime .NET Core sont utilisées lorsque plusieurs runtimes sont installés côte à côte.

## <a name="net-core-3xtabnetcore3x"></a>[.NET Core 3.x](#tab/netcore3x)

À compter de .NET Core 3,0, les règles suivantes s’appliquent lors de la détermination de la version du kit de développement logiciel (SDK) à utiliser :

- Si aucun fichier *global. JSON* n’est trouvé, ou si *global. JSON* ne spécifie pas une version du kit de développement logiciel (SDK) ou une valeur `allowPrerelease`, la version la plus récente du kit de développement logiciel (SDK) est utilisée (équivalent à la définition de `rollForward` à `latestMajor`). La prise en compte des versions du kit de développement logiciel (SDK) préliminaires dépend de la façon dont `dotnet` est appelée.
  - Si vous **n’êtes pas** dans Visual Studio, les versions préliminaires sont prises en compte.
  - Si vous êtes dans Visual Studio, il utilise l’état de préversion demandé. Autrement dit, si vous utilisez une préversion de Visual Studio ou que vous définissez l’option **utiliser des aperçus de l’kit SDK .net Core** ( **sous outils** > **options** > **environnement** > **fonctionnalités**en préversion), les versions préliminaires sont prises en compte. dans le cas contraire, seules les versions release sont prises en compte.
- Si un fichier *global. JSON* qui ne spécifie pas une version du kit de développement logiciel (SDK) est trouvé et qu’il spécifie une valeur `allowPrerelease`, la version la plus récente du kit de développement logiciel (SDK) est utilisée (ce qui équivaut à définir `rollForward` sur `latestMajor`) La version la plus récente du kit de développement logiciel (SDK) peut être Release ou version préliminaire dépend de la valeur de `allowPrerelease`. `true` indique que les versions préliminaires sont prises en compte. `false` indique que seules les versions release sont prises en compte.
- Si un fichier *global. JSON* est trouvé et qu’il spécifie une version du kit de développement logiciel (SDK) :

  - Si aucune valeur de `rollFoward` n’est définie, elle utilise `latestPatch` comme stratégie de `rollForward` par défaut. Sinon, vérifiez chaque valeur et son comportement dans la section [restauration par progression](#rollforward) .
  - Si les versions préliminaires sont prises en compte et quel est le comportement par défaut quand `allowPrerelease` n’est pas défini est décrit dans la section [allowPrerelease](#allowprerelease) .

## <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Dans le SDK .NET Core 2. x, les règles suivantes s’appliquent lors de la détermination de la version du kit de développement logiciel (SDK) à utiliser :

- Si aucun fichier *global.json* n’est trouvé ou que *global.json* ne spécifie pas de version du kit SDK, la dernière version installée du kit SDK est utilisée. La dernière version du kit de développement logiciel (SDK) peut être Release ou version préliminaire : le numéro de version le plus élevé gagne.
- Si la version du kit SDK n’est pas spécifiée dans *global.json* :
  - Si la version spécifiée du kit SDK se trouve sur la machine, c’est cette même version qui est utilisée.
  - Si la version spécifiée du kit SDK est introuvable sur la machine, c’est la dernière **version corrective** installée du kit SDK qui est utilisée. La dernière **version du correctif** SDK installée peut être Release ou version préliminaire (le numéro de version le plus élevé gagne). Dans .NET Core 2.1 et ultérieur, les **versions correctives** antérieures à la **version corrective** spécifiée sont ignorées dans la sélection du kit SDK.
  - Dans le cas où ni la version spécifiée du kit SDK, ni une **version corrective** appropriée du kit SDK n’est trouvée, une erreur est générée.

La version du kit de développement logiciel (SDK) est composée des éléments suivants :

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

La **future version** du kit SDK .NET Core est représentée par le premier chiffre (`x`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. En règle générale, le cycle de lancement du kit SDK .NET Core est plus rapide que celui de .NET Core.

La **version corrective** est définie par les deux derniers chiffres (`yz`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. Par exemple, si vous spécifiez la version `2.1.300` du kit SDK, le mécanisme de sélection du kit SDK trouve la version `2.1.399`, mais la version `2.1.400` n’est pas considérée comme une version corrective de la version `2.1.300`.

Les versions du kit SDK .NET Core comprises entre `2.1.100` et `2.1.201` ont été lancées pendant la période transitoire entre les modèles de numérotation des versions et ne gèrent pas correctement la notation `xyz`. Si vous spécifiez ces versions dans le fichier *global.json*, nous vous recommandons vivement de vérifier que les versions spécifiées se trouvent sur les machines cibles.

---

## <a name="troubleshooting-build-warnings"></a>Résolutions des problèmes liés aux avertissements de build

> [!WARNING]
> Vous utilisez une préversion du kit SDK .NET Core. Vous pouvez définir la version du kit SDK via un fichier global.json dans le projet actif. Pour plus d’informations, consultez <https://go.microsoft.com/fwlink/?linkid=869452>

Cet avertissement indique que votre projet a été compilé à l’aide d’une version préliminaire du kit SDK .NET Core. Les versions du kit SDK .NET Core jouissent d’une image et d’un engagement de qualité. Toutefois, si vous ne souhaitez pas utiliser une version préliminaire, vérifiez les différentes stratégies que vous pouvez utiliser avec le kit de développement logiciel (SDK) .NET Core 3,0 ou une version ultérieure dans la section [allowPrerelease](#allowprerelease) . Pour les ordinateurs sur lesquels le runtime ou le kit de développement logiciel (SDK) .NET Core 3,0 ou version ultérieure n’a jamais été installé, vous devez créer un fichier *global. JSON* et spécifier la version exacte que vous souhaitez utiliser.

> [!WARNING]
> Le projet de démarrage '{startupProject}' cible le framework '.NETCoreApp' version '{targetFrameworkVersion}'. Cette version des outils en ligne de commande Entity Framework Core .NET prend uniquement en charge la version 2.0 ou supérieure. Pour plus d’informations sur l’utilisation d’anciennes versions des outils, consultez <https://go.microsoft.com/fwlink/?linkid=871254>.

À partir du kit SDK .NET Core 2.1 (version 2.1.300), la commande `dotnet ef` est incluse dans le kit SDK. Cet avertissement indique que votre projet cible EF Core 1.0 ou 1.1, qui n’est pas compatible avec le kit SDK .NET Core 2.1 (et les versions ultérieures). Pour compiler votre projet, installez le kit SDK .NET Core 2.0 (version 2.1.201) ou une version antérieure sur votre ordinateur et définissez la version du SDK à utiliser dans le fichier *global.json*. Pour plus d’informations sur la commande `dotnet ef`, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Voir aussi

- [Méthode de résolution des kits SDK de projet](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
