---
ms.openlocfilehash: ae9ba8aaf842c6607020abf76c981266f5c4dd61
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67856956"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>Amélioration de la validation des certificats de confiance des chaînes WCF pour l’authentification de certificat Net.Tcp

|   |   |
|---|---|
|Détails|.NET Framework 4.7.2 améliore la validation des certificats de confiance des chaînes lors de l’utilisation de l’authentification de certificat avec la sécurité de transport avec WCF. Avec cette amélioration, les certificats clients utilisés pour s’authentifier auprès d’un serveur doivent être configurés pour l’authentification client.  De même, les certificats de serveur pour l’authentification d’un serveur doivent être configurés pour l’authentification serveur. Avec ce changement, si le certificat racine est désactivé, la validation de chaîne de certificat échoue. Le même changement a également été effectué pour .NET Framework 3.5 et versions ultérieures par le biais du déploiement de sécurité Windows. Vous trouverez plus d’informations [ici](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7). Ce changement est activé par défaut et peut être désactivé par un paramètre de configuration.|
|Suggestion|<ul><li>Vérifiez si votre certification serveur et client a l’OID EKU nécessaire. Si ce n’est pas le cas, mettez à jour votre certification.</li><li>Vérifiez si votre certificat racine est valide. Si ce n’est pas le cas, mettez-le à jour.</li><li>Comment ignorer ce changement : si vous ne pouvez pas mettre à jour le certificat, vous pouvez contourner temporairement ce changement cassant avec le paramètre de configuration suivant. Toutefois, si vous choisissez d’ignorer ce changement, vous exposez votre système au problème de sécurité.</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.7.2|
|Type|Runtime|

