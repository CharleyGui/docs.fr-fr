---
title: 'Modification avec rupture : éblouissant : prise en charge mise à jour du navigateur'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée éblouissant : prise en charge du navigateur mise à jour'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 63b35aa8cb73bfb82c565007704375bac3737299
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761225"
---
# <a name="blazor-updated-browser-support"></a>Éblouissant : prise en charge mise à jour du navigateur

ASP.NET Core 5,0 introduit de [nouvelles fonctionnalités éblouissantes](https://github.com/dotnet/aspnetcore/issues/21514), dont certaines ne sont pas compatibles avec les navigateurs plus anciens. La liste des navigateurs pris en charge par éblouissant dans ASP.NET Core 5,0 a été mise à jour en conséquence.

Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="old-behavior"></a>Ancien comportement

Le serveur éblouissant prend en charge Microsoft Internet Explorer 11 avec des polyremplissages suffisants. Le serveur éblouissant et le webassembly éblouissant sont également fonctionnels dans l' [héritage Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).

## <a name="new-behavior"></a>Nouveau comportement

Le serveur éblouissant dans ASP.NET Core 5,0 n’est pas pris en charge avec Microsoft Internet Explorer 11. Le serveur éblouissant et l’webassembly éblouissant ne sont pas entièrement fonctionnels dans l’héritage Microsoft Edge.

## <a name="reason-for-change"></a>Motif de modification

Les nouvelles fonctionnalités éblouissantes de ASP.NET Core 5,0 ne sont pas compatibles avec ces anciens navigateurs, et l’utilisation de ces anciens navigateurs diminue. Pour plus d’informations, consultez les ressources suivantes :

* [Le support Windows pour l’héritage Microsoft Edge se termine également le 9 mars 2021](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [Les applications et services Microsoft 365 prendront en charge Microsoft Internet Explorer 11 le 17 août 2021](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a>Action recommandée

Effectuez une mise à niveau à partir de ces anciens navigateurs vers le [nouveau Microsoft Edge basé sur le chrome](https://www.microsoft.com/edge). Pour les applications éblouissantes qui doivent prendre en charge ces anciens navigateurs, utilisez ASP.NET Core 3,1. La liste des navigateurs pris en charge pour éblouissant dans ASP.NET Core 3,1 n’a pas changé et est documentée sur les [plateformes prises en charge](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).

## <a name="affected-apis"></a>API affectées

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
