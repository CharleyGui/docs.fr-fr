---
ms.openlocfilehash: 8b804d23247b95381f3ff83bc12c32215a420fb6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614611"
---
### <a name="wpf-appdomain-shutdown-handling-may-now-call-dispatcherinvoke-in-cleanup-of-weak-events"></a>La gestion de l’arrêt de l’AppDomain dans WPF peut maintenant appeler répartiteur. Invoke en nettoyage des événements faibles

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, WPF crée potentiellement un <xref:System.Windows.Threading.Dispatcher?displayProperty=nameWithType> sur le thread finaliseur .net pendant l’arrêt d’AppDomain.  Ce problème a été résolu dans .NET Framework 4.7.2 et les versions ultérieures en faisant en sorte que le nettoyage des événements faibles prenne en charge les threads.  En raison de cela, WPF peut appeler <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> pour terminer le processus de nettoyage. Dans certaines applications, cette modification du minutage du finaliseur peut entraîner des exceptions lors de l’arrêt du processus ou de l’AppDomain.  Cela se produit généralement dans les applications qui n’arrêtent pas correctement les répartiteurs exécutés sur les threads de travail avant l’arrêt du processus ou de l’AppDomain.  De telles applications doivent prendre soin de gérer correctement la durée de vie des répartiteurs.

#### <a name="suggestion"></a>Suggestion

Dans .NET Framework 4.7.2 et les versions ultérieures, les développeurs peuvent désactiver ce correctif afin d’éviter les problèmes de synchronisation (mais pas d’éliminer) susceptibles de se produire en raison de la modification du nettoyage. Pour désactiver la modification de nettoyage, utilisez l’indicateur AppContext suivant.<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotInvokeInWeakEventTableShutdownListener=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |
