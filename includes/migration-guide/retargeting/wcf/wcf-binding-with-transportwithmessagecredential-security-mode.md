---
ms.openlocfilehash: 2359dafb9042c13ae75e644d4ea655f53c14e95e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804311"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Liaison WCF avec le mode de sécurité TransportWithMessageCredential

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6.1, il est possible de configurer une liaison WCF qui utilise le mode de sécurité TransportWithMessageCredential pour recevoir des messages avec des en-têtes &quot;to&quot; non signés pour les clés de sécurité asymétriques. Par défaut, les en-têtes &quot;to&quot; non signés continueront à être rejetés dans .NET Framework 4.6.1. Ils seront acceptés uniquement si une application accepte ce nouveau mode de fonctionnement en utilisant le commutateur de configuration Switch.System.ServiceModel.AllowUnsignedToHeader.|
|Suggestion|Parce qu’il s’agit d’une fonctionnalité d’abonnement, le comportement des applications existantes ne devrait pas être affecté.<br/>Pour contrôler si le nouveau comportement est utilisé ou non, utilisez le paramètre de configuration suivant :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Transparent|
|Version|4.6.1|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|
