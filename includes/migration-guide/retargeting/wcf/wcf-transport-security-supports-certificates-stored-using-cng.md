---
ms.openlocfilehash: b57e0acb03a99f33460a7b6c880280b37e01a17b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859281"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>La sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, la sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG). Cette prise en charge se limite aux certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible .NET Framework 4.6.2, cette fonctionnalité est activée par défaut. Dans les versions antérieures du .NET Framework, les tentatives d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent une exception.|
|Suggestion|Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures mais qui s’exécutent sur .NET Framework 4.6.2 peuvent activer la prise en charge des certificats CNG en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou web.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Vous pouvez en faire autant par programmation avec un code de ce type :<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Notez qu’en raison de cette modification, tout code de traitement des exceptions qui dépend de l’échec de la tentative d’établissement d’une communication sécurisée avec un certificat CNG ne s’exécutera plus.|
|Étendue|Secondaire|
|Version|4.6.2|
|Type|Reciblage|
