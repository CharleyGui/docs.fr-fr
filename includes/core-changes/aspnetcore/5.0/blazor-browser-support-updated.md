---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804922"
---
### <a name="blazor-updated-browser-support"></a>Éblouissant : prise en charge mise à jour du navigateur

ASP.NET Core 5,0 introduit de [nouvelles fonctionnalités éblouissantes](https://github.com/dotnet/aspnetcore/issues/21514), dont certaines ne sont pas compatibles avec les navigateurs plus anciens. La liste des navigateurs pris en charge par éblouissant dans ASP.NET Core 5,0 a été mise à jour en conséquence.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).

#### <a name="version-introduced"></a>Version introduite

5.0

#### <a name="old-behavior"></a>Ancien comportement

Le serveur éblouissant prend en charge Microsoft Internet Explorer 11 avec des polyremplissages suffisants. Le serveur éblouissant et le webassembly éblouissant sont également fonctionnels dans l' [héritage Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).

#### <a name="new-behavior"></a>Nouveau comportement

Le serveur éblouissant dans ASP.NET Core 5,0 n’est pas pris en charge avec Microsoft Internet Explorer 11. Le serveur éblouissant et l’webassembly éblouissant ne sont pas entièrement fonctionnels dans l’héritage Microsoft Edge.

#### <a name="reason-for-change"></a>Motif de modification

Les nouvelles fonctionnalités éblouissantes de ASP.NET Core 5,0 ne sont pas compatibles avec ces anciens navigateurs, et l’utilisation de ces anciens navigateurs diminue. Pour plus d’informations, consultez les ressources suivantes :

* [Le support Windows pour l’héritage Microsoft Edge se termine également le 9 mars 2021](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Les applications et services Microsoft 365 prendront en charge Microsoft Internet Explorer 11 le 17 août 2021](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a>Action recommandée

Effectuez une mise à niveau à partir de ces anciens navigateurs vers le [nouveau Microsoft Edge basé sur le chrome](https://www.microsoft.com/edge). Pour les applications éblouissantes qui doivent prendre en charge ces anciens navigateurs, utilisez ASP.NET Core 3,1. La liste des navigateurs pris en charge pour éblouissant dans ASP.NET Core 3,1 n’a pas changé et est documentée sur les [plateformes prises en charge](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
