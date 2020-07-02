---
ms.openlocfilehash: 0024b2a53444319788b8cdd312d537f994070b5e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614510"
---
### <a name="sslstream-supports-tls-alerts"></a>SslStream prend en charge les alertes TLS

#### <a name="details"></a>Détails

Après l’échec d’une négociation TLS, un <xref:System.IO.IOException?displayProperty=fullName> avec une exception <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> interne est levé par la première opération d’E/S de lecture/écriture. Le <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> Code du <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> peut être mappé à l’alerte TLS à partir du tiers distant à l’aide des [codes d’erreur Schannel pour les alertes TLS et SSL](https://docs.microsoft.com/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Pour plus d’informations, consultez [RFC 2246 : section 7.2.2 alertes d’erreur](https://tools.ietf.org/html/rfc2246#section-7.2.2). <br/>Dans .NET Framework 4.6.2 et les versions antérieures, le comportement est l’expiration du canal de transport (généralement une connexion TCP) pendant une opération de lecture ou d’écriture si l’autre partie n’est pas parvenue à négocier la connexion et l’a rejetée immédiatement après.

#### <a name="suggestion"></a>Suggestion

Les applications qui appellent des API d’E/S réseau comme <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> doivent gérer <xref:System.IO.IOException> ou <xref:System.TimeoutException?displayProperty=fullName>.<br/>La fonctionnalité des alertes TLS est activée par défaut à compter de .NET Framework 4.7. Afin de préserver la compatibilité, cette fonctionnalité est désactivée pour les applications ciblant .NET Framework 4.0 à .NET Framework 4.6.2 qui s’exécutent sur un système .NET Framework 4.7 ou ultérieur. <br/>L’API de configuration suivante est disponible pour activer ou désactiver la fonctionnalité pour les applications .NET Framework 4.6 et ultérieures s’exécutant sur .NET Framework 4.7 ou version ultérieure.

- Par programme : doit être la première chose que fait l’application puisque ServicePointManager ne s’initialise qu’une seule fois :

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- AppConfig :

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- Clé de Registre (ordinateur global) : définissez la valeur sur `false` pour activer la fonctionnalité dans .NET Framework 4,6-4.6.2.

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,7         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
