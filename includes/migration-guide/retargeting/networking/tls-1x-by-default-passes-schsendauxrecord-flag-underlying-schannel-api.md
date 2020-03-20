---
ms.openlocfilehash: fc17efbad63ee43ddcdfd14e2fbd1557d2b3d31c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72424774"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1.x passe par défaut l’indicateur SCH_SEND_AUX_RECORD à l’API SCHANNEL sous-jacente

|   |   |
|---|---|
|Détails|Quand vous utilisez TLS 1.x, le .NET Framework s’appuie sur l’API SCHANNEL Windows sous-jacente. À compter de .NET Framework 4.6, l’indicateur [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) est passé par défaut à SCHANNEL. Cela amène SCHANNEL à fractionner les données à chiffrer en deux enregistrements distincts, le premier sous forme d’un octet unique et le second sous forme de <em>n</em>-1 octets. Dans de rares cas, cela interrompt la communication entre les clients et les serveurs existants qui supposent que les données résident dans un seul enregistrement.|
|Suggestion|Si ce changement interrompt la communication avec un serveur existant, vous pouvez désactiver l’envoi de l’indicateur [SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/win32/api/schannel/ns-schannel-schannel_cred) et restaurer le comportement précédent qui ne divise pas les données en enregistrements distincts en ajoutant le commutateur suivant à l’élément [<](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) de la section [<](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante. Son utilisation à d’autres fins n’est pas recommandée.</blockquote> |
|Étendue|Edge|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|
