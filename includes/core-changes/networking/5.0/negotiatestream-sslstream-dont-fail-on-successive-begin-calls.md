---
ms.openlocfilehash: 16994e9cd97b31a30c8c5ce49d2042ff79b3f60b
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050514"
---
### <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a><span data-ttu-id="9a7ad-101">NegotiateStream et SslStream autorisent les opérations Begin successives</span><span class="sxs-lookup"><span data-stu-id="9a7ad-101">NegotiateStream and SslStream allow successive Begin operations</span></span>

<span data-ttu-id="9a7ad-102">Les cas d’erreur sur les flux de sécurité sont gérés différemment, et les appels successifs à `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` peuvent ne plus échouer.</span><span class="sxs-lookup"><span data-stu-id="9a7ad-102">Error cases on security streams are handled differently, and successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` may no longer fail.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a7ad-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9a7ad-103">Version introduced</span></span>

<span data-ttu-id="9a7ad-104">5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="9a7ad-104">5.0 RC1</span></span>

#### <a name="change-description"></a><span data-ttu-id="9a7ad-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="9a7ad-105">Change description</span></span>

<span data-ttu-id="9a7ad-106">Dans les versions précédentes de .NET, l’appel de ou, de manière `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` consécutive, sans commencer `EndAuthenticateAsServer` par appeler ou `EndAuthenticateAsClient` engendre un <xref:System.NotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="9a7ad-106">In previous .NET versions, calling `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` successively without first calling `EndAuthenticateAsServer` or `EndAuthenticateAsClient` results in a <xref:System.NotSupportedException>.</span></span> <span data-ttu-id="9a7ad-107">À compter de .NET 5,0, les appels successifs à `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` n’aboutissent plus à un <xref:System.NotSupportedException> , car ces API sont soutenus par une <xref:System.Threading.Tasks.Task> implémentation basée sur.</span><span class="sxs-lookup"><span data-stu-id="9a7ad-107">Starting in .NET 5.0, successive calls to `BeginAuthenticateAsServer` or `BeginAuthenticateAsClient` no longer result in a <xref:System.NotSupportedException>, because these APIs are backed by a <xref:System.Threading.Tasks.Task>-based implementation.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9a7ad-108">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="9a7ad-108">Reason for change</span></span>

<span data-ttu-id="9a7ad-109">Le basculement de l’implémentation interne du modèle de programmation asynchrone (APM) vers basé sur repose sur les <xref:System.Threading.Tasks.Task> performances et réduit la complexité du code.</span><span class="sxs-lookup"><span data-stu-id="9a7ad-109">Switching the internal implementation from asynchronous programming model (APM) to <xref:System.Threading.Tasks.Task>-based improves performance and decreases code complexity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a7ad-110">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9a7ad-110">Recommended action</span></span>

<span data-ttu-id="9a7ad-111">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="9a7ad-111">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="9a7ad-112">Category</span><span class="sxs-lookup"><span data-stu-id="9a7ad-112">Category</span></span>

<span data-ttu-id="9a7ad-113">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="9a7ad-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a7ad-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="9a7ad-114">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

-->
