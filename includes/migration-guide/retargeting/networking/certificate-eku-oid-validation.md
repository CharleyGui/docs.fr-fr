---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615677"
---
### <a name="certificate-eku-oid-validation"></a>Validation de l’OID de l’utilisation améliorée de la clé (EKU) du certificat

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6, les classes <xref:System.Net.Security.SslStream> ou <xref:System.Net.ServicePointManager> effectuent la validation de l’identificateur d’objet (OID) de l’utilisation améliorée de la clé (EKU). Une extension EKU (utilisation améliorée de la clé) est une collection d’identificateurs d’objet indiquant les applications qui utilisent la clé. La validation de l’OID d’utilisation améliorée de la clé (EKU) utilise des rappels de certificat distant pour garantir que le certificat distant a les OID corrects pour l’utilisation prévue.

#### <a name="suggestion"></a>Suggestion

Si cette modification n’est pas souhaitable, vous pouvez désactiver la validation de l’OID de l’EKU de certificat en ajoutant le commutateur suivant à [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) dans le [`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) de votre fichier de configuration d’application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante. Son utilisation à d’autres fins n’est pas recommandée.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
