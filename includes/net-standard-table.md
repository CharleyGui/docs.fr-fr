---
ms.openlocfilehash: 9b8d28f7f5508b4ba7c46306b5e78aa3d53d95e0
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71263342"
---
| .NET Standard              | [1.0]  | [1.1]  | [1.2] | [1.3] | [1.4] | [1.5]              | [1.6]              | [2.0]               | [2.1] |
|----------------------------|--------|--------|-------|-------|-------|--------------------|--------------------|---------------------|---------------------
| .NET Core                  | 1.0    | 1.0    | 1.0   | 1.0   | 1.0   | 1.0                | 1.0                | 2.0                 | 3.0 |
| .NET Framework <sup>1</sup>| 4.5    | 4.5    | 4.5.1 | 4.6   | 4.6.1 | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup> | 4.6.1 <sup>2</sup>  | NON APPLICABLE<sup>3</sup> |
| Mono                       | 4.6    | 4.6    | 4.6   | 4.6   | 4.6   | 4.6                | 4.6                | 5,4                 | 6.4 |
| Xamarin.iOS                | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0               | 10.0               | 10.14               | 12.16 |
| Xamarin.Mac                | 3.0    | 3.0    | 3.0   | 3.0   | 3.0   | 3.0                | 3.0                | 3.8                 | 5,16 |
| Xamarin.Android            | 7.0    | 7.0    | 7.0   | 7.0   | 7.0   | 7.0                | 7.0                | 8.0                 | 10.0 |
| Plateforme Windows universelle | 10.0   | 10.0   | 10.0  | 10.0  | 10.0  | 10.0.16299         | 10.0.16299         | 10.0.16299          | TBD |
| Unity                      | 2018.1 | 2018.1 | 2018.1| 2018.1| 2018.1| 2018.1             |  2018.1            | 2018.1              | TBD |

<sup>1. Les versions listées pour .NET Framework s’appliquent au kit SDK .NET Core 2.0 et aux versions ultérieures des outils. Les versions antérieures utilisent un autre mappage pour .NET Standard 1.5 et versions ultérieures. Vous pouvez [télécharger les outils pour Outils .NET Core pour Visual Studio 2015](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md) si vous ne pouvez pas mettre à niveau vers Visual Studio 2017.</sup>

<sup>2 Les versions listées ici représentent les règles que NuGet utilise pour déterminer si une bibliothèque .NET Standard donnée est applicable. Même si NuGet considère que .NET Framework 4.6.1 prend en charge .NET Standard 1.5 à 2.0, il existe plusieurs problèmes avec la consommation des bibliothèques .NET Standard qui ont été créées pour ces versions à partir de projets .NET Framework 4.6.1. Pour les projets .NET Framework qui doivent utiliser ces bibliothèques, nous vous recommandons de les mettre à niveau en ciblant .NET Framework 4.7.2 ou ultérieur.</sup>

<sup>3 Le .NET Framework ne prend pas en charge .NET Standard version 2.1 ou ultérieures. Pour plus d’informations, consultez l’[annonce de .NET Standard 2.1](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-1/).</sup>

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
