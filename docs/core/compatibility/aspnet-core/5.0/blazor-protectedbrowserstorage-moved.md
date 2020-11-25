---
title: 'Modification avec rupture : éblouissant : fonctionnalité ProtectedBrowserStorage déplacée vers l’infrastructure partagée'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée « éblouissant » : fonctionnalité ProtectedBrowserStorage déplacée vers le Framework partagé'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760967"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a>Éblouissant : fonctionnalité ProtectedBrowserStorage déplacée vers le Framework partagé

Dans le cadre de la version ASP.NET Core 5,0 RC2, la `ProtectedBrowserStorage` fonctionnalité a été déplacée vers le ASP.net Core Framework partagé.

## <a name="version-introduced"></a>Version introduite

5,0 RC2

## <a name="old-behavior"></a>Ancien comportement

Dans ASP.NET Core 5,0 Preview 8, la fonctionnalité est disponible en tant que partie du package [Microsoft. AspNetCore. Components. Web. extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) , mais n’est utilisable que dans le webassembly éblouissant.

Dans ASP.NET Core RC1 5,0, la fonctionnalité est disponible dans le package [Microsoft. AspNetCore. Components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) , qui fait référence à l' `Microsoft.AspNetCore.App` infrastructure partagée.

## <a name="new-behavior"></a>Nouveau comportement

Dans ASP.NET Core RC2 5,0, une référence de package NuGet n’est plus nécessaire pour référencer et utiliser la fonctionnalité.

## <a name="reason-for-change"></a>Motif de modification

Le passage à l’infrastructure partagée est mieux adapté à l’expérience utilisateur que les clients attendent.

## <a name="recommended-action"></a>Action recommandée

Si vous effectuez une mise à niveau à partir de ASP.NET Core 5,0 RC1, procédez comme suit :

1. Supprimez la `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` référence de package du projet.
1. Remplacez `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` par `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. Supprimez l’appel à `AddProtectedBrowserStorage` de votre `Startup` classe.

Si vous effectuez une mise à niveau à partir de ASP.NET Core 5,0 Preview 8, procédez comme suit :

1. Supprimez la `Microsoft.AspNetCore.Components.Web.Extensions` référence de package du projet.
1. Remplacez `using Microsoft.AspNetCore.Components.Web.Extensions;` par `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.
1. Supprimez l’appel à `AddProtectedBrowserStorage` de votre `Startup` classe.

## <a name="affected-apis"></a>API affectées

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
