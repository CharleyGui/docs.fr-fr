---
ms.openlocfilehash: 9fd4e570d9476f5ac4c310759113d72b354a3060
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606868"
---
### <a name="tls-1x-by-default-passes-the-sch_send_aux_record-flag-to-the-underlying-schannel-api"></a>TLS 1.x passe par défaut l’indicateur SCH_SEND_AUX_RECORD à l’API SCHANNEL sous-jacente

#### <a name="details"></a>Détails

Quand vous utilisez TLS 1.x, le .NET Framework s’appuie sur l’API SCHANNEL Windows sous-jacente. À compter de .NET Framework 4.6, l’indicateur [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) est passé par défaut à SCHANNEL. Cela amène SCHANNEL à fractionner les données à chiffrer en deux enregistrements distincts, le premier sous forme d’un octet unique et le second sous forme de <em>n</em>-1 octets. Dans de rares cas, cela interrompt la communication entre les clients et les serveurs existants qui supposent que les données résident dans un seul enregistrement.

#### <a name="suggestion"></a>Suggestion

Si ce changement interrompt la communication avec un serveur existant, vous pouvez désactiver l’envoi de l’indicateur [SCH_SEND_AUX_RECORD](/windows/win32/api/schannel/ns-schannel-schannel_cred) et restaurer le comportement précédent qui ne divise pas les données en enregistrements distincts en ajoutant le commutateur suivant à l’élément [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) de la section [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchSendAuxRecord=true" />
</runtime>
```

> [!IMPORTANT]
> Ce paramètre est fourni dans le seul but d’assurer la compatibilité descendante. Son utilisation à d’autres fins n’est pas recommandée.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
