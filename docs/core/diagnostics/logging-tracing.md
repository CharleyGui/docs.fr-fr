---
title: Journalisation et suivi-.NET Core
description: Présentation de la journalisation et du suivi de .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 06781c6a5c1d771b1fa772539705cd1e2b3ad2d4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "70234642"
---
# <a name="net-core-logging-and-tracing"></a>Journalisation et suivi .NET Core

La journalisation et le suivi sont en fait deux noms pour la même technique. La technique simple a été utilisée depuis les premiers jours d’ordinateurs. Cela implique simplement l’instrumentation d’une application pour écrire la sortie à consommer ultérieurement.

## <a name="reasons-to-use-logging-and-tracing"></a>Raisons pour utiliser la journalisation et le suivi

Cette technique simple est étonnamment puissante. Il peut être utilisé dans les situations où un débogueur échoue:

- Les problèmes survenant sur de longues périodes de temps peuvent être difficiles à déboguer avec un débogueur traditionnel. Les journaux permettent d’obtenir des informations détaillées sur de longues périodes de temps. En revanche, les débogueurs sont limités à l’analyse en temps réel.
- Les applications multithread et les applications distribuées sont souvent difficiles à déboguer.  L’attachement d’un débogueur tend à modifier les comportements. Les journaux détaillés peuvent être analysés en fonction des besoins pour comprendre les systèmes complexes.
- Les problèmes dans les applications distribuées peuvent provenir d’une interaction complexe entre de nombreux composants et il n’est pas judicieux de connecter un débogueur à chaque partie du système.
- De nombreux services ne doivent pas être bloqués. L’attachement d’un débogueur provoque souvent des échecs de dépassement de délai.
- Les problèmes ne sont pas toujours prévus. La journalisation et le suivi sont conçus pour une faible surcharge, afin que les programmes puissent toujours être enregistrées en cas de problème.

## <a name="net-core-apis"></a>API .NET Core

### <a name="print-style-apis"></a>API de style d’impression

Les <xref:System.Console?displayProperty=nameWithType>classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, et<xref:System.Diagnostics.Debug?displayProperty=nameWithType> fournissent chacune des API de style d’impression similaires pratiques pour la journalisation.

Vous avez le choix de l’API de style d’impression à utiliser. Les principales différences sont les suivantes:
- <xref:System.Console?displayProperty=nameWithType>
  - Toujours activé et écrit toujours sur la console.
  - Utile pour les informations que votre client peut avoir besoin de voir dans la version.
  - Étant donné qu’il s’agit de l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc. Ce code de débogage n’est souvent jamais archivé dans le contrôle de code source.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Activé uniquement lorsque `TRACE` est défini.
  - Écrit dans attaché <xref:System.Diagnostics.Trace.Listeners>, par <xref:System.Diagnostics.DefaultTraceListener>défaut.
  - Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des builds.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Activé uniquement lorsque `DEBUG` est défini.
  - Écrit dans un débogueur attaché.
  - Lors `*nix` de l’écriture dans `COMPlus_DebugWriteToStdErr` stderr si est défini.
  - Utilisez cette API lors de la création de journaux qui seront activés uniquement dans les versions Debug.

### <a name="logging-events"></a>Journalisation des événements

Les API suivantes sont plus orientées événement. Au lieu d’enregistrer des chaînes simples, elles consignent des objets d’événement.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource est l’API principale de suivi .NET Core racine.
  - Disponible dans toutes les versions de .NET Standard.
  - Autorise uniquement le suivi des objets sérialisables.
  - Écrit dans les [écouteurs d’événements](xref:System.Diagnostics.Tracing.EventListener)attachés.
  - .NET Core fournit des écouteurs pour:
    - EventPipe de .NET Core sur toutes les plateformes
    - [Suivi d’v nements pour Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Infrastructure de suivi LTTng pour Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Inclus dans .NET Core et en tant que [package NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.
  - Permet le suivi en cours des objets non sérialisables.
  - Comprend un pont pour permettre l’écriture de champs sélectionnés d’objets journalisés dans <xref:System.Diagnostics.Tracing.EventSource>un.

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Fournit un moyen définitif d’identifier les messages du journal qui résultent d’une activité ou d’une transaction spécifique. Cet objet peut être utilisé pour mettre en corrélation les journaux entre différents services.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Windows uniquement.
  - Écrit des messages dans le journal des événements Windows.
  - Les administrateurs système attendent que des messages d’erreur d’application irrécupérables s’affichent dans le journal des événements Windows.

## <a name="ilogger-and-logging-frameworks"></a>Frameworks ILogger et Logging

Les API de bas niveau ne sont peut-être pas le bon choix pour vos besoins de journalisation. Vous pouvez envisager d’utiliser un Framework de journalisation.

L' <xref:Microsoft.Extensions.Logging.ILogger> interface a été utilisée pour créer une interface de journalisation commune dans laquelle les enregistreurs d’événements peuvent être insérés via l’injection de dépendances.

Par exemple, pour vous permettre de choisir le meilleur choix pour votre application `ASP.NET` , vous pouvez prendre en charge une sélection de frameworks intégrés et tiers:
- [ASP.NET intégrés aux fournisseurs de journalisation](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET fournisseurs de journalisation tiers](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Références associées à la journalisation

- [Guide pratique : effectuer une compilation conditionnelle avec Trace et Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Guide pratique : Ajouter des instructions de suivi au code d’application](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- La [journalisation ASP.net](/aspnet/core/fundamentals/logging) fournit une vue d’ensemble des techniques de journalisation qu’elle prend en charge.

- L’interpolation de chaîne peut simplifier l’écriture du code de journalisation. [ C# ](../../csharp/language-reference/tokens/interpolated.md)

- La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour la journalisation des exceptions.

- La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.

## <a name="performance-considerations"></a>Considérations relatives aux performances

La mise en forme des chaînes peut prendre un temps de traitement de l’UC notable.

Dans les applications critiques pour les performances, il est recommandé de:
- Évitez un grand nombre de journaux quand aucun n’est à l’écoute. Évitez de créer des messages de journalisation coûteux en vérifiant si la journalisation est activée en premier.
- Consignez uniquement ce qui est utile.
- Différer la mise en forme complète à l’étape d’analyse.
