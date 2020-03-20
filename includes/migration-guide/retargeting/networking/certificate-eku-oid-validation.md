---
ms.openlocfilehash: ee9bba91a2c4e11bd005fedb8adf0c2e7c7b0d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804468"
---
### <a name="certificate-eku-oid-validation"></a>Validation de l’OID de l’utilisation améliorée de la clé (EKU) du certificat

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6, les classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> effectuent la validation de l’identificateur d’objet (OID) de l’utilisation améliorée de la clé (EKU). Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé. La validation de l’OID d’utilisation améliorée de la clé (EKU) utilise des rappels de certificat distant pour garantir que le certificat distant a les OID corrects pour l’utilisation prévue.|
|Suggestion|Si cette modification n’est pas souhaitable, vous pouvez désactiver la validation EKU OID en ajoutant le commutateur suivant [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) à [ \<l’AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans le fichier de configuration de votre application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante. Son utilisation à d’autres fins n’est pas recommandée.</blockquote> |
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
