---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451882"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="06665-101">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="06665-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="06665-102">La valeur par défaut de <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> la propriété est passée de 2,0 à 1,1.</span><span class="sxs-lookup"><span data-stu-id="06665-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06665-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="06665-103">Version introduced</span></span>

<span data-ttu-id="06665-104">3.0</span><span class="sxs-lookup"><span data-stu-id="06665-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="06665-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="06665-105">Change description</span></span>

<span data-ttu-id="06665-106">Dans .NET Core 1,0 à 2,0, la valeur par défaut de <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> la propriété est 1,1.</span><span class="sxs-lookup"><span data-stu-id="06665-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="06665-107">À compter de .NET Core 2,1, il a été remplacé par 2,1.</span><span class="sxs-lookup"><span data-stu-id="06665-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="06665-108">À compter de .NET Core 3,0, le numéro de version par défaut <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retourné par la propriété est encore une fois 1,1.</span><span class="sxs-lookup"><span data-stu-id="06665-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06665-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="06665-109">Recommended action</span></span>

<span data-ttu-id="06665-110">Mettez à jour votre code s’il dépend <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> de la propriété qui retourne une valeur par défaut de 2,0.</span><span class="sxs-lookup"><span data-stu-id="06665-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="06665-111">Category</span><span class="sxs-lookup"><span data-stu-id="06665-111">Category</span></span>

<span data-ttu-id="06665-112">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="06665-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06665-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="06665-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
