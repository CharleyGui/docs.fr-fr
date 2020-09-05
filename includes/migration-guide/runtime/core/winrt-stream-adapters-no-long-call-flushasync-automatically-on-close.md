---
ms.openlocfilehash: 2b4f35fe15f806897e5e4d85ee774b2e4572d974
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497465"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>Les adaptateurs de flux WinRT n’appellent plus FlushAsync automatiquement lors de la fermeture

#### <a name="details"></a>Détails

Dans les applications du Windows Store, les adaptateurs de flux Windows Runtime n’appellent plus la méthode FlushAsync à partir de la méthode Dispose.

#### <a name="suggestion"></a>Suggestion

Cette modification devrait être transparente. Les développeurs peuvent rétablir le comportement précédent en écrivant du code comme le suivant :<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
