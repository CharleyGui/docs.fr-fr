---
title: Vue d’ensemble de global.json
description: Découvrez comment utiliser le fichier global.json pour définir la version du kit SDK .NET Core pendant l’exécution de commandes CLI .NET Core.
ms.date: 04/21/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 5384b59cccb629a5409d26a8df7c81b3999fc95f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021353"
---
# <a name="globaljson-overview"></a>Vue d’ensemble de global.json

**Cet article s’applique à:** ✔️ .NET Core 2.0 SDK et les versions ultérieures

Le fichier *global.json* vous permet de définir la version du kit SDK .NET Core utilisée pendant l’exécution des commandes de l’interface CLI .NET Core. La sélection du kit SDK .NET Core est indépendante de la spécification du runtime ciblé par votre projet. La version SDK core .NET indique quelles versions de l’IFC core .NET est utilisée.

En général, vous souhaitez utiliser la dernière version des outils SDK, donc aucun fichier *global.json* n’est nécessaire. Dans certains scénarios avancés, vous voudrez peut-être contrôler la version des outils SDK, et cet article explique comment le faire.

Pour plus d’informations sur la spécification du runtime, consultez [Versions cibles de .NET Framework](../../standard/frameworks.md).

Le kit SDK .NET Core recherche un fichier *global.json* dans le répertoire de travail actif (qui n’est pas nécessairement le même que le répertoire du projet) ou dans l’un de ses répertoires parents.

## <a name="globaljson-schema"></a>Schéma de global.json

### <a name="sdk"></a>SDK

Entrez : `object`

Spécifie des informations sur le kit SDK .NET Core à sélectionner.

#### <a name="version"></a>version

- Entrez : `string`

- Disponible depuis: .NET Core 1.0 SDK.

Version du kit SDK .NET Core à utiliser.

Ce domaine:

- N’a pas de support wildcard, c’est-à-dire que le numéro de version complet doit être spécifié.
- Ne prend pas en charge les plages de versions.

#### <a name="allowprerelease"></a>autoriserPrerelease

- Entrez : `boolean`

- Disponible depuis: .NET Core 3.0 SDK.

Indique si le résolveur SDK doit tenir compte des versions préreléase lors de la sélection de la version SDK à utiliser.

Si vous ne définissez pas cette valeur explicitement, la valeur par défaut dépend si vous êtes en cours d’exécution à partir de Visual Studio:

- Si vous n’êtes **pas** dans Visual `true`Studio, la valeur par défaut est .
- Si vous êtes dans Visual Studio, il utilise le statut de prérédition demandé. Autrement dit, si vous utilisez une version Aperçu de Visual Studio ou si vous définissez les **aperçus d’utilisation de l’option .NET Core SDK** (sous **tools** > **Options** > **Environment** > **Preview Features**), la valeur par défaut est `true`; autrement, `false`.

#### <a name="rollforward"></a>rollForward

- Entrez : `string`

- Disponible depuis: .NET Core 3.0 SDK.

La stratégie de déploiement à utiliser lors de la sélection d’une version SDK, soit comme un repli lorsqu’une version spécifique SDK est manquante ou comme une directive pour utiliser une version supérieure. Une [version](#version) doit être `rollForward` spécifiée avec une valeur, sauf si vous la définissez à `latestMajor`.

Pour comprendre les politiques disponibles et leur comportement, considérez les `x.y.znn`définitions suivantes pour une version SDK dans le format :

- `x`est la version principale.
- `y`est la version mineure.
- `z`est le groupe de longs métrages.
- `nn`est la version patch.

Le tableau suivant montre les `rollForward` valeurs possibles pour la clé :

| Valeur         | Comportement |
| ------------- | ---------- |
| `patch`       | Utilise la version spécifiée. <br> S’il n’est pas trouvé, roule vers l’avant vers le dernier niveau de patch. <br> S’il n’est pas trouvé, échoue. <br><br> Cette valeur est le comportement hérité des versions antérieures de la SDK. |
| `feature`     | Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif. <br> S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans le même majeur / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, échoue. |
| `minor`       | Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif. <br> S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans la même version majeure / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, roule vers l’avant à la prochaine plus haute bande mineure et fonctionnalité dans le même majeur et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, échoue. |
| `major`       | Utilise le dernier niveau de patch pour la bande majeure spécifiée, mineure, et de dispositif. <br> S’il n’est pas trouvé, roule vers l’avant à la bande de fonctionnalité supérieure suivante dans la même version majeure / mineur et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, roule vers l’avant à la prochaine plus haute bande mineure et fonctionnalité dans le même majeur et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, roule vers l’avant à la prochaine bande supérieure majeure, mineure, et fonctionnalité et utilise le dernier niveau de patch pour cette bande de fonctionnalité. <br> S’il n’est pas trouvé, échoue. |
| `latestPatch` | Utilise le dernier niveau de patch installé qui correspond à la bande de majeur, mineure et de fonctionnalité demandée avec un niveau de patch et qui est plus ou égale que la valeur spécifiée. <br> S’il n’est pas trouvé, échoue. |
| `latestFeature` | Utilise la bande de fonctionnalité et le niveau de patch les plus élevés qui correspondent au majeur et au mineur demandés avec une bande de fonctionnalités supérieure ou égale à la valeur spécifiée. <br> S’il n’est pas trouvé, échoue. |
| `latestMinor` | Utilise le mineur installé le plus haut, bande de fonctionnalité, et le niveau de patch qui correspond à la majeure demandée avec un mineur qui est plus ou égal que la valeur spécifiée. <br> S’il n’est pas trouvé, échoue. |
| `latestMajor` | Utilise le SDK de base le plus élevé installé .NET avec une majeure qui est supérieure ou égale à la valeur spécifiée. <br> S’il n’est pas trouvé, échouez. |
| `disable`     | Il ne roule pas en avant. Correspondance exacte requise. |

## <a name="examples"></a>Exemples

L’exemple suivant montre comment ne pas utiliser les versions prérelease :

```json
{
  "sdk": {
    "allowPrerelease": false
  }
}
```

L’exemple suivant montre comment utiliser la version la plus élevée installée qui est supérieure ou égale à la version spécifiée :

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestMajor"
  }
}
```

L’exemple suivant montre comment utiliser la version spécifiée exacte :

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "disable"
  }
}
```

L’exemple suivant montre comment utiliser la dernière bande de fonctionnalités et la version patch installée d’une version majeure et mineure spécifique :

```json
{
  "sdk": {
    "version": "3.1.000",
    "rollForward": "latestFeature"
  }
}
```

L’exemple suivant montre comment utiliser la version patch la plus élevée installée d’une version spécifique (sous la forme, 3.1.1xx):

```json
{
  "sdk": {
    "version": "3.1.100",
    "rollForward": "latestPatch"
  }
}
```

## <a name="globaljson-and-the-net-core-cli"></a>global.JSON et l’interface CLI .NET Core

Il est utile de savoir quelles versions SDK sont installées sur votre machine pour en définir une dans le fichier *global.json.* Pour plus d’informations sur la façon de le faire, voir [Comment vérifier que .NET Core est déjà installé](../install/how-to-detect-installed-versions.md#check-sdk-versions).

Pour installer d’autres versions SDK core .NET supplémentaires sur votre machine, visitez la page [Télécharger .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)

Vous pouvez créer un fichier *global.json* dans le répertoire actif en exécutant la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :

```dotnetcli
dotnet new globaljson --sdk-version 3.0.100
```

## <a name="matching-rules"></a>Règles de correspondance

> [!NOTE]
> Les règles de correspondance `dotnet.exe` sont régies par le point d’entrée, qui est commun à tous les runtimes installés .NET Core installé. Les règles de correspondance pour la dernière version installée du .NET Core Runtime sont utilisées lorsque vous avez plusieurs temps d’exécution installés côte à côte.

## <a name="net-core-3x"></a>[.NET Core 3.x](#tab/netcore3x)

En commençant par .NET Core 3.0, les règles suivantes s’appliquent lorsqu’elles déterminent la version du SDK à utiliser :

- Si aucun fichier *global.json* n’est trouvé, ou *global.json* ne `allowPrerelease` spécifie pas une version SDK `latestMajor`ni une valeur, la version SDK installée la plus élevée est utilisée (équivalent à la mise à). `rollForward` La question de savoir si les versions `dotnet` SDK préreléase sont considérées dépend de la façon dont elles sont invoquées.
  - Si vous n’êtes **pas** dans Visual Studio, les versions prérelease sont prises en considération.
  - Si vous êtes dans Visual Studio, il utilise le statut de prérédition demandé. Autrement dit, si vous utilisez une version Aperçu de Visual Studio ou si vous définissez les **aperçus d’utilisation de l’option .NET Core SDK** (sous **tools** > **Options** > **Environment** > Preview**Features**), les versions préreléase sont envisagées; autrement, seules les versions de version sont prises en considération.
- Si un fichier *global.json* est trouvé qui ne spécifie `allowPrerelease` pas une version SDK mais il spécifie une valeur, la version SDK installée la plus élevée est utilisée (équivalent au réglage `rollForward` à `latestMajor`). Si la dernière version SDK peut être libéré ou `allowPrerelease`prérelease dépend de la valeur de . `true`indique que les versions préreléase sont envisagées; `false` indique que seules les versions de version sont prises en considération.
- Si un fichier *global.json* est trouvé et il spécifie une version SDK:

  - Si `rollFoward` aucune valeur n’est définie, elle s’utilise `latestPatch` comme stratégie par défaut. `rollForward` Sinon, vérifiez chaque valeur et leur comportement dans la section [rollForward.](#rollforward)
  - Si les versions prérelease sont considérées `allowPrerelease` et quel est le comportement par défaut quand n’est pas défini est décrit dans la section [allowPrerelease.](#allowprerelease)

## <a name="net-core-2x"></a>[.NET Core 2.x](#tab/netcore2x)

Dans .NET Core 2.x SDK, les règles suivantes s’appliquent lorsqu’elles déterminent quelle version du SDK utiliser :

- Si aucun fichier *global.json* n’est trouvé ou que *global.json* ne spécifie pas de version du kit SDK, la dernière version installée du kit SDK est utilisée. La dernière version SDK peut être soit la libération ou la prérénée - le nombre de versions la plus élevée gagne.
- Si la version du kit SDK n’est pas spécifiée dans *global.json* :
  - Si la version spécifiée du kit SDK se trouve sur la machine, c’est cette même version qui est utilisée.
  - Si la version spécifiée du kit SDK est introuvable sur la machine, c’est la dernière **version corrective** installée du kit SDK qui est utilisée. La dernière version installée de **patch** SDK peut être soit la libération ou la prérénée - le nombre de version le plus élevé gagne. Dans .NET Core 2.1 et ultérieur, les **versions correctives** antérieures à la **version corrective** spécifiée sont ignorées dans la sélection du kit SDK.
  - Dans le cas où ni la version spécifiée du kit SDK, ni une **version corrective** appropriée du kit SDK n’est trouvée, une erreur est générée.

La version SDK est composée des parties suivantes :

`[.NET Core major version].[.NET Core minor version].[xyz][-optional preview name]`

La **future version** du kit SDK .NET Core est représentée par le premier chiffre (`x`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. En règle générale, le cycle de lancement du kit SDK .NET Core est plus rapide que celui de .NET Core.

La **version corrective** est définie par les deux derniers chiffres (`yz`) de la dernière partie du nombre (`xyz`) pour les versions 2.1.100 et ultérieures du kit SDK. Par exemple, si vous spécifiez la version `2.1.300` du kit SDK, le mécanisme de sélection du kit SDK trouve la version `2.1.399`, mais la version `2.1.400` n’est pas considérée comme une version corrective de la version `2.1.300`.

Les versions du kit SDK .NET Core comprises entre `2.1.100` et `2.1.201` ont été lancées pendant la période transitoire entre les modèles de numérotation des versions et ne gèrent pas correctement la notation `xyz`. Si vous spécifiez ces versions dans le fichier *global.json*, nous vous recommandons vivement de vérifier que les versions spécifiées se trouvent sur les machines cibles.

---

## <a name="troubleshoot-build-warnings"></a>Avertissements de construction de dépanneurs

* L’avertissement suivant indique que votre projet a été compilé à l’aide d’une version préréactive du SDK core .NET :

  > Vous utilisez une préversion du kit SDK .NET Core. Vous pouvez définir la version du kit SDK via un fichier global.json dans le projet actif. Plus <https://go.microsoft.com/fwlink/?linkid=869452>à .

  Les versions du kit SDK .NET Core jouissent d’une image et d’un engagement de qualité. Toutefois, si vous ne voulez pas utiliser une version préréactivease, vérifiez les différentes stratégies que vous pouvez utiliser avec le .NET Core 3.0 SDK ou une version ultérieure dans la section [allowPrerelease.](#allowprerelease) Pour les machines qui n’ont jamais eu un .NET Core 3.0 ou plus Runtime ou SDK installé, vous devez créer un fichier *global.json* et spécifier la version exacte que vous voulez utiliser.

* L’avertissement suivant indique que votre projet cible EF Core 1.0 ou 1.1, ce qui n’est pas compatible avec .NET Core 2.1 SDK et les versions ultérieures :

  > Le projet de démarrage '{startupProject}' cible le framework '.NETCoreApp' version '{targetFrameworkVersion}'. Cette version des outils en ligne de commande Entity Framework Core .NET prend uniquement en charge la version 2.0 ou supérieure. Pour plus d’informations sur l’utilisation des anciennes versions des outils, voir <https://go.microsoft.com/fwlink/?linkid=871254>.

  À partir du kit SDK .NET Core 2.1 (version 2.1.300), la commande `dotnet ef` est incluse dans le kit SDK. Pour compiler votre projet, installez .NET Core 2.0 SDK (version 2.1.201) ou plus tôt sur votre machine et définissez la version SDK souhaitée à l’aide du fichier *global.json.* Pour plus d’informations sur la commande `dotnet ef`, consultez [Outils en ligne de commande EF Core .NET](/ef/core/miscellaneous/cli/dotnet).

## <a name="see-also"></a>Voir aussi

- [Méthode de résolution des kits SDK de projet](/visualstudio/msbuild/how-to-use-project-sdk#how-project-sdks-are-resolved)
