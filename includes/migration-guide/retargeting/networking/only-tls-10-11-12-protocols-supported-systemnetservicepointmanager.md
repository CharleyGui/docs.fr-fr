---
ms.openlocfilehash: 5b531dc23feb311a797823dfa2a4d853859f9e18
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235546"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>Seuls les protocoles TLS 1.0, 1.1 et 1.2 sont pris en charge dans System.Net.ServicePointManager et System.Net.Security.SslStream

|   |   |
|---|---|
|Détails|À compter de .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager> et <xref:System.Net.Security.SslStream> ne peuvent utiliser que l’un des trois protocoles suivants : Tls1.0, Tls1.1 ou Tls1.2. Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.|
|Suggestion|L’atténuation recommandée consiste à mettre à niveau l’application côté serveur vers TLS 1.0, TLS 1.1 ou TLS 1.2. Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext?displayProperty=name> peut être utilisée pour désactiver cette fonctionnalité de deux manières :<ol><li>En définissant des commutateurs de compatibilité programmatiquement sur <xref:System.AppContext?displayProperty=name>, comme expliqué [ici](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>En ajoutant la ligne suivante à la section <code>&lt;runtime&gt;</code> du fichier app.config :</li></ol><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;&#13;&#10;</code></pre>|
|Portée|Mineur|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
