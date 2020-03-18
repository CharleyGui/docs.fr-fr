---
ms.openlocfilehash: 9e95db8a1530fabd30b5344c87728b9210c0ad69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802832"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | N/A<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5.4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5.16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Plateforme Windows universelle | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1 Les versions répertoriées pour .NET Framework s’appliquent à .NET Core 2.0 SDK et aux versions ultérieures de l’outillage. Les anciennes versions utilisaient une cartographie différente pour .NET Standard 1.5 et plus. Vous pouvez [télécharger l’outillage pour les outils .NET Core pour Visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) si vous ne pouvez pas passer à Visual Studio 2017 ou une version ultérieure.</sup>

<sup>2 Les versions énumérées ici représentent les règles que NuGet utilise pour déterminer si une bibliothèque standard .NET donnée est applicable. Bien que NuGet considère .NET Framework 4.6.1 comme soutenant .NET Standard 1.5 à 2.0, il ya plusieurs problèmes avec la consommation .NET bibliothèques standard qui ont été construits pour ces versions à partir de .NET Framework 4.6.1 projets. Pour les projets cadre .NET qui doivent utiliser ces bibliothèques, nous vous recommandons de mettre à niveau le projet pour cibler .NET Framework 4.7.2 ou plus.</sup>

<sup>3 .NET Framework ne supporte pas .NET Standard 2.1 ou versions ultérieures. Pour plus de détails, voir [l’annonce de .NET Standard 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

- Les colonnes représentent les versions de .NET Standard. Chaque cellule d’en-tête est un lien vers un document qui indique les API ajoutées à cette version de .NET Standard.
- Les lignes représentent les différentes implémentations .NET.
- Le numéro de version dans chaque cellule indique la version *minimale* de l’implémentation nécessaire pour cibler cette version de .NET Standard.
- Pour un tableau interactif, consultez [Versions .NET Standard](https://dotnet.microsoft.com/platform/dotnet-standard#versions).

[1.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.0.md
[1.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.1.md
[1.2]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.2.md
[1.3]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.3.md
[1.4]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.4.md
[1.5]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.5.md
[1.6]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard1.6.md
[2.0]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md
[2.1]: https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.1.md
