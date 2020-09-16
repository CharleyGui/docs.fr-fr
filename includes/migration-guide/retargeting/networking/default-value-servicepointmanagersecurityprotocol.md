---
ms.openlocfilehash: 8aff4b1aa329d6fdfebf3b62e9279e9dfe5de0a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606870"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>La valeur par défaut de ServicePointManager.SecurityProtocol est SecurityProtocolType.System.Default

#### <a name="details"></a>Détails

À partir des applications qui ciblent .NET Framework 4.7, la valeur par défaut de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> est <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Ce changement permet aux API de réseau .NET Framework basées sur SslStream (comme FTP, HTTPS et SMTP) d’hériter des protocoles de sécurité par défaut du système d’exploitation au lieu d’utiliser des valeurs codées en dur définies par le .NET Framework. La valeur par défaut varie en fonction du système d’exploitation et des configurations personnalisées effectuées par l’administrateur système. Pour plus d’informations sur le protocole Schannel par défaut dans chaque version du système d’exploitation Windows, consultez [Protocols in TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Pour les applications qui ciblent une version antérieure de .NET Framework, la valeur par défaut de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> dépend de la version de .NET Framework ciblée. Pour plus d’informations, consultez la [section Mise en réseau de la rubrique Modifications de reciblage pour la migration de .NET Framework 4.5.2 vers la version 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking).

#### <a name="suggestion"></a>Suggestion

Ce changement affecte les applications qui ciblent .NET Framework 4.7 ou versions ultérieures. Si vous préférez utiliser un protocole défini, au lieu de vous appuyer sur la valeur par défaut du système, vous pouvez définir explicitement la valeur de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>. Si cette modification n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration à la [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section de votre fichier de configuration de l’application. L’exemple suivant montre la section `<runtime>` et l’option d’annulation `Switch.System.Net.DontEnableSystemDefaultTlsVersions` :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,7         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>
