---
ms.openlocfilehash: 7b86365e841defb78558b10fa171a88031b4820e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859202"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a>La valeur par défaut de ServicePointManager.SecurityProtocol est SecurityProtocolType.System.Default

|   |   |
|---|---|
|Détails|À partir des applications qui ciblent .NET Framework 4.7, la valeur par défaut de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> est <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>. Ce changement permet aux API de réseau .NET Framework basées sur SslStream (comme FTP, HTTPS et SMTP) d’hériter des protocoles de sécurité par défaut du système d’exploitation au lieu d’utiliser des valeurs codées en dur définies par le .NET Framework. La valeur par défaut varie en fonction du système d’exploitation et des configurations personnalisées effectuées par l’administrateur système. Pour plus d’informations sur le protocole Schannel par défaut dans chaque version du système d’exploitation Windows, consultez [Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</p>Pour les applications qui ciblent une version antérieure de .NET Framework, la valeur par défaut de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> dépend de la version de .NET Framework ciblée. Pour plus d’informations, consultez la [section Mise en réseau de la rubrique Modifications de reciblage pour la migration de .NET Framework 4.5.2 vers la version 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking).|
|Suggestion|Ce changement affecte les applications qui ciblent .NET Framework 4.7 ou versions ultérieures. </br>Si vous préférez utiliser un protocole défini, au lieu de vous appuyer sur la valeur par défaut du système, vous pouvez définir explicitement la valeur de la propriété <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>.</br>Si ce changement n’est pas souhaitable, vous pouvez choisir de l’annuler en ajoutant un paramètre de configuration à la section [<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de votre application. L’exemple suivant montre la section <code>&lt;runtime&gt;</code> et l’option d’annulation <code>Switch.System.Net.DontEnableSystemDefaultTlsVersions</code> :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSystemDefaultTlsVersions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.7|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType></li></ul>|

