---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615691"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="bec0b-101">Seuls les protocoles TLS 1.0, 1.1 et 1.2 sont pris en charge dans System.Net.ServicePointManager et System.Net.Security.SslStream</span><span class="sxs-lookup"><span data-stu-id="bec0b-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="bec0b-102">Détails</span><span class="sxs-lookup"><span data-stu-id="bec0b-102">Details</span></span>

<span data-ttu-id="bec0b-103">À compter de .NET Framework 4.6, les classes <xref:System.Net.ServicePointManager> et <xref:System.Net.Security.SslStream> ne peuvent utiliser que l’un des trois protocoles suivants : TLS 1.0, TLS 1.1 ou TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="bec0b-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="bec0b-104">Le protocole SSL 3.0 et le chiffrement RC4 ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bec0b-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bec0b-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="bec0b-105">Suggestion</span></span>

<span data-ttu-id="bec0b-106">L’atténuation recommandée consiste à mettre à niveau l’application côté serveur vers TLS 1.0, TLS 1.1 ou TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="bec0b-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="bec0b-107">Si ce n'est pas possible, ou si les applications clientes sont interrompues, la classe <xref:System.AppContext?displayProperty=fullName> peut être utilisée pour désactiver cette fonctionnalité de deux manières :</span><span class="sxs-lookup"><span data-stu-id="bec0b-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="bec0b-108">En définissant des commutateurs de compatibilité par programmation sur le <xref:System.AppContext?displayProperty=fullName> , comme expliqué [ici](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span><span class="sxs-lookup"><span data-stu-id="bec0b-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="bec0b-109">En ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="bec0b-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="bec0b-110">Nom</span><span class="sxs-lookup"><span data-stu-id="bec0b-110">Name</span></span>    | <span data-ttu-id="bec0b-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="bec0b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bec0b-112">Étendue</span><span class="sxs-lookup"><span data-stu-id="bec0b-112">Scope</span></span>   | <span data-ttu-id="bec0b-113">Secondaire</span><span class="sxs-lookup"><span data-stu-id="bec0b-113">Minor</span></span>       |
| <span data-ttu-id="bec0b-114">Version</span><span class="sxs-lookup"><span data-stu-id="bec0b-114">Version</span></span> | <span data-ttu-id="bec0b-115">4.6</span><span class="sxs-lookup"><span data-stu-id="bec0b-115">4.6</span></span>         |
| <span data-ttu-id="bec0b-116">Type</span><span class="sxs-lookup"><span data-stu-id="bec0b-116">Type</span></span>    | <span data-ttu-id="bec0b-117">Reciblage</span><span class="sxs-lookup"><span data-stu-id="bec0b-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bec0b-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="bec0b-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
