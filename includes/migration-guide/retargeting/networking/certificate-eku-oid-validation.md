---
ms.openlocfilehash: 0ddd554aa114395085a9f8ff41a99ca9a6096a51
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804468"
---
### <a name="certificate-eku-oid-validation"></a>Validation de l’OID de l’utilisation améliorée de la clé (EKU) du certificat

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6, les classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> effectuent la validation de l’identificateur d’objet (OID) de l’utilisation améliorée de la clé (EKU). Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé. La validation de l’OID d’utilisation améliorée de la clé (EKU) utilise des rappels de certificat distant pour garantir que le certificat distant a les OID corrects pour l’utilisation prévue.|
|Suggestion|Si ce changement n’est pas souhaitable, vous pouvez désactiver la validation de l’OID de l’utilisation améliorée de la clé (EKU) du certificat en ajoutant le commutateur suivant à l’élément [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) du [ ` ](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontCheckCertificateEKUs=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante. Son utilisation à d’autres fins n’est pas recommandée.</blockquote> |
|Portée|Mineur|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

