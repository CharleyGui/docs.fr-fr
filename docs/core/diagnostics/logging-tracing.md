---
title: Journalisation et suivi-.NET Core
description: Présentation de la journalisation et du suivi de .NET Core.
ms.date: 10/12/2020
ms.openlocfilehash: 9af04cceeef3fbfb8392eb91667c21374511548a
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94687581"
---
# <a name="net-core-logging-and-tracing"></a>Journalisation et suivi .NET Core

La journalisation et le suivi sont en fait deux noms pour la même technique. La technique simple a été utilisée depuis les premiers jours d’ordinateurs. Cela implique simplement l’instrumentation d’une application pour écrire la sortie à consommer ultérieurement.

## <a name="reasons-to-use-logging-and-tracing"></a>Raisons pour utiliser la journalisation et le suivi

Cette technique simple est étonnamment puissante. Il peut être utilisé dans les situations où un débogueur échoue :

- Les problèmes survenant sur de longues périodes peuvent être difficiles à déboguer avec un débogueur traditionnel. Les journaux permettent d’obtenir des informations détaillées sur de longues périodes. En revanche, les débogueurs se limitent à une analyse en temps réel.
- Les applications multithread et les applications distribuées sont souvent difficiles à déboguer.  Attacher un débogueur tend à modifier les comportements. Les journaux détaillés peuvent être analysés en fonction des besoins pour comprendre les systèmes complexes.
- Les problèmes dans les applications distribuées peuvent provenir d’une interaction complexe entre de nombreux composants, et il n’est pas judicieux de connecter un débogueur à chaque partie du système.
- De nombreux services ne devraient pas être bloqués. Attacher un débogueur provoque souvent des échecs de dépassement de délai.
- Les problèmes ne sont pas toujours anticipés. La journalisation et le suivi sont conçus pour entraîner une faible surcharge, afin que les programmes puissent toujours enregistrer les données en cas de problème.

## <a name="net-core-apis"></a>API .NET Core

### <a name="print-style-apis"></a>API de style d’impression

Les <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType> classes, et <xref:System.Diagnostics.Debug?displayProperty=nameWithType> fournissent chacune des API de style d’impression similaires pratiques pour la journalisation.

Vous avez le choix de l’API de style d’impression à utiliser. :

- <xref:System.Console?displayProperty=nameWithType>
  - Toujours activé et toujours écrire dans la console.
  - C’est approche est utile pour les informations dont votre client peut avoir besoin lors de la mise en production.
  - Comme il s’agit de l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc. Souvent, ce code de débogage n’est jamais archivé dans le contrôle de code source.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Activé uniquement quand `TRACE` est défini.
  - Écrit dans attaché <xref:System.Diagnostics.Trace.Listeners> , par défaut <xref:System.Diagnostics.DefaultTraceListener> .
  - Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des builds.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Activé uniquement quand `DEBUG` est défini.
  - Écrit dans un débogueur attaché.
  - Lors de l' `*nix` écriture dans stderr si `COMPlus_DebugWriteToStdErr` est défini.
  - Utilisez cette API lors de la création de journaux qui seront activés uniquement dans les builds de débogage.

### <a name="logging-events"></a>Journalisation des événements

Les API suivantes sont plus orientées événement. Au lieu d’enregistrer des chaînes simples, elles consignent des objets d’événement.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource est l’API principale de suivi .NET Core racine.
  - Disponible dans toutes les versions de .NET Standard.
  - Autorise uniquement le suivi des objets sérialisables.
  - Peut être consommé dans le processus via n’importe quelle instance [EventListener](xref:System.Diagnostics.Tracing.EventListener) configurée pour utiliser EventSource.
  - Peut être consommé hors processus via :
    - [EventPipe de .net Core](./eventpipe.md) sur toutes les plateformes
    - [Suivi d’événements pour Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Infrastructure de suivi LTTng pour Linux](https://lttng.org/)
      - Procédure pas à pas : [collecte d’une trace LTTng à l’aide de PerfCollect](trace-perfcollect-lttng.md).

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Inclus dans .NET Core et en tant que [package NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.
  - Permet le suivi en cours des objets non sérialisables.
  - Comprend un pont pour permettre l’écriture de champs sélectionnés d’objets journalisés dans un <xref:System.Diagnostics.Tracing.EventSource> .

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Fournit un moyen définitif d’identifier les messages du journal qui résultent d’une activité ou d’une transaction spécifique. Cet objet peut être utilisé pour mettre en corrélation les journaux entre différents services.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Windows uniquement.
  - Écrit des messages dans le journal des événements Windows.
  - Les administrateurs système attendent que des messages d’erreur d’application irrécupérables s’affichent dans le journal des événements Windows.

## <a name="ilogger-and-logging-frameworks"></a>Frameworks ILogger et Logging

Les API de bas niveau ne sont peut-être pas le bon choix pour vos besoins de journalisation. Vous pouvez envisager d’utiliser un Framework de journalisation.

L' <xref:Microsoft.Extensions.Logging.ILogger> interface a été utilisée pour créer une interface de journalisation commune dans laquelle les enregistreurs d’événements peuvent être insérés via l’injection de dépendances.

Par exemple, pour vous permettre de choisir le meilleur choix pour votre application, .NET offre une prise en charge pour une sélection de frameworks intégrés et tiers :

- [Fournisseurs de journalisation intégrés .NET](../extensions/logging-providers.md#built-in-logging-providers)
- [Fournisseurs de journalisation tiers .NET](../extensions/logging-providers.md#third-party-logging-providers)

## <a name="logging-related-references"></a>Références associées à la journalisation

- [Procédure : Effectuer une compilation conditionnelle avec Trace et Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Procédure : Ajouter des instructions de trace dans le code d’une application](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- La [journalisation dans .net](../extensions/logging.md) fournit une vue d’ensemble des techniques de journalisation qu’il prend en charge.

- L' [interpolation de chaîne C#](../../csharp/language-reference/tokens/interpolated.md) peut simplifier l’écriture d’un code de journalisation.

- La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour la journalisation des exceptions.

- La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.

## <a name="performance-considerations"></a>Considérations relatives aux performances

La mise en forme des chaînes peut prendre un temps de traitement de l’UC notable.

Dans les applications critiques pour les performances, il est recommandé de :

- Évitez un grand nombre de journaux quand aucun n’est à l’écoute. Évitez de créer des messages de journalisation coûteux en vérifiant si la journalisation est activée en premier.
- Consignez uniquement ce qui est utile.
- Différer la mise en forme complète à l’étape d’analyse.
