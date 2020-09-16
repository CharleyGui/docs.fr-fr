---
ms.openlocfilehash: aadf5eb85c8736c29639d49bc8baf21545d2467c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606873"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM marshale avec succès les paramètres ByRef SafeArray sur les événements

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.2 et versions antérieures, le marshaling en code natif d’un paramètre ByRef [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) sur un événement COM était voué à l’échec.  Avec cette modification, le [SafeArray](/windows/desktop/api/oaidl/ns-oaidl-safearray) est maintenant correctement marshalé.<ul><li>[ x ] Quirked</li></ul>

#### <a name="suggestion"></a>Suggestion

Si les paramètres ByRef SafeArray correctement marshalés sur des événements COM interromptent l’exécution, vous pouvez désactiver ce code en ajoutant le commutateur de configuration suivant à la configuration de votre application :<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
