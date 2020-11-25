---
title: 'Modification avec rupture : extensions : modifications de référence de package affectant certains packages NuGet'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core extensions 5,0 intitulées : modifications de référence de package affectant certains packages NuGet'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 4a525d9f7aad4409fd507fcf80c00968ff4b63d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760963"
---
# <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Extensions : modifications de référence de package affectant certains packages NuGet

Avec la migration de certains `Microsoft.Extensions.*` packages NuGet du référentiel [dotnet/extensions](https://github.com/dotnet/extensions) vers [dotnet/Runtime](https://github.com/dotnet/runtime), comme décrit dans [ASPNET/announcements # 411](https://github.com/aspnet/Announcements/issues/411), les modifications d’empaquetage sont appliquées à certains des packages migrés. Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 4

## <a name="old-behavior"></a>Ancien comportement

Certains `Microsoft.Extensions.*` packages incluent des références de package pour les API sur lesquelles votre application s’appuie.

## <a name="new-behavior"></a>Nouveau comportement

Votre application doit peut-être ajouter des `Microsoft.Extensions.*` dépendances de package.

## <a name="reason-for-change"></a>Motif de modification

Les stratégies d’empaquetage ont été mises à jour pour mieux s’aligner avec le référentiel *dotnet/Runtime* . Dans la nouvelle stratégie, les références de package inutilisées sont supprimées des fichiers *. nupkg* lors de l’empaquetage.

## <a name="recommended-action"></a>Action recommandée

Les consommateurs des packages concernés doivent ajouter une dépendance directe sur la dépendance de package supprimée dans leur projet si les API de la dépendance de package supprimée sont utilisées. Le tableau suivant répertorie les packages affectés et les modifications correspondantes.

|Nom du package|Description de la modification|
|------------|------------------|
|[Microsoft.Extensions.Configfiguration. Classeur](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Suppression de la référence à `Microsoft.Extensions.Configuration`|
|[Microsoft.Extensions.Configuration.Js](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Suppression de la référence à `System.Threading.Tasks.Extensions`|
|[Microsoft. extensions. Hosting. Abstracts](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Suppression de la référence à `Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft.Extensions.Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Suppression de la référence à `Microsoft.Extensions.Configuration.Binder`|
|[Microsoft. extensions. Logging. console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Suppression de la référence à `Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft. extensions. Logging. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |Référence supprimée à `System.Diagnostics.EventLog` pour le moniker du Framework cible .NET Framework 4.6.1|
|[Microsoft. extensions. Logging. EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Suppression de la référence à `System.Threading.Tasks.Extensions`|
|[Microsoft. extensions. options](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Suppression de la référence à `System.ComponentModel.Annotations`|

Par exemple, la référence de package à `Microsoft.Extensions.Configuration` a été supprimée de `Microsoft.Extensions.Configuration.Binder` . Aucune API de la dépendance n’a été utilisée dans le package. Les utilisateurs de `Microsoft.Extensions.Configuration.Binder` qui dépendent des API de `Microsoft.Extensions.Configuration` doivent ajouter une référence directe à celui-ci dans leur projet.

## <a name="affected-apis"></a>API affectées

None

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
