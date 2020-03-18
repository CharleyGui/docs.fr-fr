---
title: Enregistrement et traçage - .NET Core
description: Une introduction à l’enregistrement et au traçage de base de .NET.
ms.date: 08/05/2019
ms.openlocfilehash: 392b88c9ea3c31c919a605ac0a5c886f7d63f79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714424"
---
# <a name="net-core-logging-and-tracing"></a>.NET Core logging and tracing

L’exploitation forestière et le traçage sont vraiment deux noms pour la même technique. La technique simple a été utilisée depuis les premiers jours des ordinateurs. Il s’agit simplement d’instrumenter une application pour écrire la sortie à consommer plus tard.

## <a name="reasons-to-use-logging-and-tracing"></a>Raisons d’utiliser l’enregistrement et le traçage

Cette technique simple est étonnamment puissante. Il peut être utilisé dans les situations où un débbuggeur échoue :

- Les problèmes qui se produisent sur de longues périodes de temps, peuvent être difficiles à déboquer avec un débbugger traditionnel. Les journaux permettent un examen post-mortem détaillé couvrant de longues périodes de temps. En revanche, les débbuggeurs sont limités à l’analyse en temps réel.
- Les applications multi-threaded et les applications distribuées sont souvent difficiles à déboiffer.  L’attachement d’un débbuggeur tend à modifier les comportements. Les journaux détaillés peuvent être analysés au besoin pour comprendre les systèmes complexes.
- Les problèmes dans les applications distribuées peuvent résulter d’une interaction complexe entre de nombreux composants et il peut ne pas être raisonnable de connecter un débbugger à chaque partie du système.
- De nombreux services ne devraient pas être bloqués. L’attachement d’un débogueur provoque souvent des échecs de délai d’attente.
- Les problèmes ne sont pas toujours prévus. L’enregistrement et le traçage sont conçus pour les frais généraux faibles afin que les programmes puissent toujours être consigné en cas de problème.

## <a name="net-core-apis"></a>.NET Core API

### <a name="print-style-apis"></a>API de style d’impression

Les <xref:System.Console?displayProperty=nameWithType> <xref:System.Diagnostics.Trace?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug?displayProperty=nameWithType> , et les classes fournissent chacune des API de style d’impression similaires pratique pour l’enregistrement.

Le choix de l’API de style d’impression à utiliser est à vous. :

- <xref:System.Console?displayProperty=nameWithType>
  - Toujours activé et écrit toujours à la console.
  - Utile pour les informations que votre client peut avoir besoin de voir dans la version.
  - Parce que c’est l’approche la plus simple, elle est souvent utilisée pour le débogage temporaire ad hoc. Ce code de débaillement n’est souvent jamais enregistré au contrôle de source.
- <xref:System.Diagnostics.Trace?displayProperty=nameWithType>
  - Activé uniquement `TRACE` lorsque vous êtes défini.
  - Écrit à <xref:System.Diagnostics.Trace.Listeners>ci-joint <xref:System.Diagnostics.DefaultTraceListener>, par défaut le .
  - Utilisez cette API lors de la création de journaux qui seront activés dans la plupart des versions.
- <xref:System.Diagnostics.Debug?displayProperty=nameWithType>
  - Activé uniquement `DEBUG` lorsque vous êtes défini.
  - Écrit à un débbuggeur attaché.
  - Sur `*nix` écrit à stderr si `COMPlus_DebugWriteToStdErr` est réglé.
  - Utilisez cette API lors de la création de journaux qui ne seront activés que dans les constructions de débogé.

### <a name="logging-events"></a>Événements d’exploitation forestière

Les API suivantes sont plus orientées vers l’événement. Plutôt que d’enregistrer des chaînes simples, ils enregistrent des objets d’événement.

- <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType>
  - EventSource est la principale racine .NET Core traçant API.
  - Disponible dans toutes les versions .NET Standard.
  - Permet seulement de retracer des objets sérialisables.
  - Écrit aux [auditeurs de l’événement ci-joint](xref:System.Diagnostics.Tracing.EventListener).
  - .NET Core fournit aux auditeurs pour :
    - .NET Core’s EventPipe sur toutes les plateformes
    - [Suivi d'événements pour Windows (ETW)](/windows/win32/etw/event-tracing-portal)
    - [Cadre de traçage LTTng pour Linux](https://lttng.org/)

- <xref:System.Diagnostics.DiagnosticSource?displayProperty=nameWithType>
  - Inclus dans .NET Core et comme un [paquet NuGet](https://www.nuget.org/packages/System.Diagnostics.DiagnosticSource) pour .NET Framework.
  - Permet le traçage en cours d’objets non sérialisables.
  - Inclut un pont pour permettre l’écriture de <xref:System.Diagnostics.Tracing.EventSource>certains champs d’objets enregistrés à un .

- <xref:System.Diagnostics.Activity?displayProperty=nameWithType>
  - Fournit un moyen définitif d’identifier les messages journalaux résultant d’une activité ou d’une transaction spécifique. Cet objet peut être utilisé pour corréler les journaux entre différents services.

- <xref:System.Diagnostics.EventLog?displayProperty=nameWithType>
  - Windows uniquement.
  - Écrit des messages au journal d’événements Windows.
  - Les administrateurs système s’attendent à ce que les messages d’erreur d’application mortels apparaissent dans le journal d’événements Windows.

## <a name="ilogger-and-logging-frameworks"></a>Cadres ILogger et exploitation forestière

Les API de bas niveau peuvent ne pas être le bon choix pour vos besoins d’enregistrement. Vous voudrez peut-être envisager un cadre d’exploitation forestière.

L’interface <xref:Microsoft.Extensions.Logging.ILogger> a été utilisée pour créer une interface d’enregistrement commune où les enregistreurs peuvent être insérés par injection de dépendance.

Par exemple, vous permettre de faire le `ASP.NET` meilleur choix pour votre application offre un support pour une sélection de cadres intégrés et tiers:

- [ASP.NET construit dans les fournisseurs d’exploitation forestière](/aspnet/core/fundamentals/logging/#built-in-logging-providers)
- [ASP.NET fournisseurs d’exploitation forestière tiers](/aspnet/core/fundamentals/logging/#third-party-logging-providers)

## <a name="logging-related-references"></a>Références liées à l’exploitation forestière

- [Comment : effectuer une compilation conditionnelle avec Trace et Debug](../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)

- [Comment : ajouter des instructions de traçage dans le code d'une application](../../framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)

- [ASP.NET l’exploitation forestière](/aspnet/core/fundamentals/logging) donne un aperçu des techniques d’exploitation forestière qu’il prend en charge.

- [L’interpolation des chaînes de CMD](../../csharp/language-reference/tokens/interpolated.md) peut simplifier l’écriture de code d’enregistrement.

- La <xref:System.Exception.Message?displayProperty=nameWithType> propriété est utile pour les exceptions d’enregistrement.

- La <xref:System.Diagnostics.StackTrace?displayProperty=nameWithType> classe peut être utile pour fournir des informations de pile dans vos journaux.

## <a name="performance-considerations"></a>Considérations relatives aux performances

La mise en forme des cordes peut prendre un temps de traitement CPU notable.

Dans les applications critiques de performance, il est recommandé que vous :

- Évitez beaucoup de connexion lorsque personne n’écoute. Évitez de construire des messages d’enregistrement coûteux en vérifiant si l’enregistrement est activé en premier.
- Enregistrez seulement ce qui est utile.
- Reportez le formatage de fantaisie à l’étape de l’analyse.
