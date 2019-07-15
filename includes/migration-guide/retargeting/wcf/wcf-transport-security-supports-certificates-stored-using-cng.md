---
ms.openlocfilehash: 8c1ca89af289dbcc6c68d5ace3e8a9f32672ec0d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859281"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a>La sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.6.2, la sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG). Cette prise en charge se limite aux certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible .NET Framework 4.6.2, cette fonctionnalité est activée par défaut. Dans les versions antérieures du .NET Framework, les tentatives d’utilisation de certificats X509 avec un fournisseur de stockage de clés CSG lèvent une exception.|
|Suggestion|Les applications qui ciblent .NET Framework 4.6.1 et les versions antérieures mais qui s’exécutent sur .NET Framework 4.6.2 peuvent activer la prise en charge des certificats CNG en ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config ou web.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableCngCertificates=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Vous pouvez en faire autant par programmation avec un code de ce type :<pre><code class="lang-cs">private const string DisableCngCertificates = @&quot;Switch.System.ServiceModel.DisableCngCertificate&quot;;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, false);&#13;&#10;</code></pre><pre><code class="lang-vb">Const DisableCngCertificates As String = &quot;Switch.System.ServiceModel.DisableCngCertificates&quot;&#13;&#10;AppContext.SetSwitch(disableCngCertificates, False)&#13;&#10;</code></pre>Notez qu’en raison de cette modification, tout code de traitement des exceptions qui dépend de l’échec de la tentative d’établissement d’une communication sécurisée avec un certificat CNG ne s’exécutera plus.|
|Portée|Mineur|
|Version|4.6.2|
|Type|Reciblage|

