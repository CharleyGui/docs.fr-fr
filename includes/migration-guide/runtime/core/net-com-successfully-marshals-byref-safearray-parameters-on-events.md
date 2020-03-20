---
ms.openlocfilehash: 6ff23bbe8c48235770d39cb7d35a1df7de6c5201
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68440263"
---
### <a name="net-com-successfully-marshals-byref-safearray-parameters-on-events"></a>.NET COM marshale avec succès les paramètres ByRef SafeArray sur les événements

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7.2 et versions antérieures, le marshaling en code natif d’un paramètre ByRef [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) sur un événement COM était voué à l’échec.  Avec cette modification, le [SafeArray](https://docs.microsoft.com/windows/desktop/api/oaidl/ns-oaidl-safearray) est maintenant correctement marshalé.<ul><li>[ x ] Quirked</li></ul>|
|Suggestion|Si les paramètres ByRef SafeArray correctement marshalés sur des événements COM interromptent l’exécution, vous pouvez désactiver ce code en ajoutant le commutateur de configuration suivant à la configuration de votre application :<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;Switch.System.Runtime.InteropServices.DoNotMarshalOutByrefSafeArrayOnInvoke&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.8|
|Type|Runtime|
