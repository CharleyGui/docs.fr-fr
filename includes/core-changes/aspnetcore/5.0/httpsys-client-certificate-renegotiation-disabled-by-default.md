---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325244"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="343a8-101">HttpSys : la renégociation de certificat client est désactivée par défaut</span><span class="sxs-lookup"><span data-stu-id="343a8-101">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="343a8-102">L’option permettant de renégocier une connexion et de demander un certificat client a été désactivée par défaut.</span><span class="sxs-lookup"><span data-stu-id="343a8-102">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="343a8-103">Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).</span><span class="sxs-lookup"><span data-stu-id="343a8-103">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="343a8-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="343a8-104">Version introduced</span></span>

<span data-ttu-id="343a8-105">ASP.NET Core 5,0</span><span class="sxs-lookup"><span data-stu-id="343a8-105">ASP.NET Core 5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="343a8-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="343a8-106">Old behavior</span></span>

<span data-ttu-id="343a8-107">La connexion peut être renégociée pour demander un certificat client.</span><span class="sxs-lookup"><span data-stu-id="343a8-107">The connection can be renegotiated to request a client certificate.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="343a8-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="343a8-108">New behavior</span></span>

<span data-ttu-id="343a8-109">Les certificats clients ne peuvent être demandés que lors de la négociation de connexion initiale.</span><span class="sxs-lookup"><span data-stu-id="343a8-109">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="343a8-110">Pour plus d’informations, consultez requête de tirage [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).</span><span class="sxs-lookup"><span data-stu-id="343a8-110">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="343a8-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="343a8-111">Reason for change</span></span>

<span data-ttu-id="343a8-112">La renégociation a entraîné un certain nombre de problèmes de performances et de blocage.</span><span class="sxs-lookup"><span data-stu-id="343a8-112">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="343a8-113">Il n’est pas non plus pris en charge dans HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="343a8-113">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="343a8-114">Pour plus de contexte lorsque l’option de contrôle de ce comportement a été introduite dans ASP.NET Core 3,1, consultez émettre [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).</span><span class="sxs-lookup"><span data-stu-id="343a8-114">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="343a8-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="343a8-115">Recommended action</span></span>

<span data-ttu-id="343a8-116">Les applications qui requièrent des certificats clients doivent utiliser *netsh.exe* pour affecter la valeur `clientcertnegotiation` à l’option `enabled` .</span><span class="sxs-lookup"><span data-stu-id="343a8-116">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="343a8-117">Pour plus d’informations, consultez [commandes netsh http](/windows-server/networking/technologies/netsh/netsh-http).</span><span class="sxs-lookup"><span data-stu-id="343a8-117">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="343a8-118">Si vous souhaitez que les certificats clients soient activés uniquement pour certaines parties de votre application, consultez les instructions à la page [certificats clients facultatifs](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span><span class="sxs-lookup"><span data-stu-id="343a8-118">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="343a8-119">Si vous avez besoin de l’ancien comportement de renégociation, définissez `HttpSysOptions.ClientCertificateMethod` sur l’ancienne valeur `ClientCertificateMethod.AllowRenegotiate` .</span><span class="sxs-lookup"><span data-stu-id="343a8-119">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="343a8-120">Cela n’est pas recommandé pour les raisons indiquées ci-dessus et dans le guide lié.</span><span class="sxs-lookup"><span data-stu-id="343a8-120">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

#### <a name="category"></a><span data-ttu-id="343a8-121">Category</span><span class="sxs-lookup"><span data-stu-id="343a8-121">Category</span></span>

<span data-ttu-id="343a8-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="343a8-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="343a8-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="343a8-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
