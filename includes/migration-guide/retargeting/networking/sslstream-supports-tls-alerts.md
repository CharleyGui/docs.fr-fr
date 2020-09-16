---
ms.openlocfilehash: 5b566dd89801caff7a253abc2fb62c5fd79591f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606512"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="c8f14-101">SslStream prend en charge les alertes TLS</span><span class="sxs-lookup"><span data-stu-id="c8f14-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="c8f14-102">Détails</span><span class="sxs-lookup"><span data-stu-id="c8f14-102">Details</span></span>

<span data-ttu-id="c8f14-103">Après l’échec d’une négociation TLS, un <xref:System.IO.IOException?displayProperty=fullName> avec une exception <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> interne est levé par la première opération d’E/S de lecture/écriture.</span><span class="sxs-lookup"><span data-stu-id="c8f14-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="c8f14-104">Le <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> Code du <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> peut être mappé à l’alerte TLS à partir du tiers distant à l’aide des [codes d’erreur Schannel pour les alertes TLS et SSL](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts). Pour plus d’informations, consultez [RFC 2246 : section 7.2.2 alertes d’erreur](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span><span class="sxs-lookup"><span data-stu-id="c8f14-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="c8f14-105">Dans .NET Framework 4.6.2 et les versions antérieures, le comportement est l’expiration du canal de transport (généralement une connexion TCP) pendant une opération de lecture ou d’écriture si l’autre partie n’est pas parvenue à négocier la connexion et l’a rejetée immédiatement après.</span><span class="sxs-lookup"><span data-stu-id="c8f14-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c8f14-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="c8f14-106">Suggestion</span></span>

<span data-ttu-id="c8f14-107">Les applications qui appellent des API d’E/S réseau comme <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> doivent gérer <xref:System.IO.IOException> ou <xref:System.TimeoutException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="c8f14-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="c8f14-108">La fonctionnalité des alertes TLS est activée par défaut à compter de .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="c8f14-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="c8f14-109">Afin de préserver la compatibilité, cette fonctionnalité est désactivée pour les applications ciblant .NET Framework 4.0 à .NET Framework 4.6.2 qui s’exécutent sur un système .NET Framework 4.7 ou ultérieur.</span><span class="sxs-lookup"><span data-stu-id="c8f14-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="c8f14-110">L’API de configuration suivante est disponible pour activer ou désactiver la fonctionnalité pour les applications .NET Framework 4.6 et ultérieures s’exécutant sur .NET Framework 4.7 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="c8f14-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="c8f14-111">Par programme : doit être la première chose que fait l’application puisque ServicePointManager ne s’initialise qu’une seule fois :</span><span class="sxs-lookup"><span data-stu-id="c8f14-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="c8f14-112">AppConfig :</span><span class="sxs-lookup"><span data-stu-id="c8f14-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="c8f14-113">Clé de Registre (ordinateur global) : définissez la valeur sur `false` pour activer la fonctionnalité dans .NET Framework 4,6-4.6.2.</span><span class="sxs-lookup"><span data-stu-id="c8f14-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="c8f14-114">Name</span><span class="sxs-lookup"><span data-stu-id="c8f14-114">Name</span></span>    | <span data-ttu-id="c8f14-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="c8f14-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c8f14-116">Étendue</span><span class="sxs-lookup"><span data-stu-id="c8f14-116">Scope</span></span>   | <span data-ttu-id="c8f14-117">Edge</span><span class="sxs-lookup"><span data-stu-id="c8f14-117">Edge</span></span>        |
| <span data-ttu-id="c8f14-118">Version</span><span class="sxs-lookup"><span data-stu-id="c8f14-118">Version</span></span> | <span data-ttu-id="c8f14-119">4,7</span><span class="sxs-lookup"><span data-stu-id="c8f14-119">4.7</span></span>         |
| <span data-ttu-id="c8f14-120">Type</span><span class="sxs-lookup"><span data-stu-id="c8f14-120">Type</span></span>    | <span data-ttu-id="c8f14-121">Reciblage</span><span class="sxs-lookup"><span data-stu-id="c8f14-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="c8f14-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="c8f14-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
