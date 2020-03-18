---
ms.openlocfilehash: 5ad9c494fd02059e05cc744aad3b06cfc9399995
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451882"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="83611-101">Valeur par défaut de HttpRequestMessage.Version changé à 1.1</span><span class="sxs-lookup"><span data-stu-id="83611-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="83611-102">La valeur par <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> défaut de la propriété est passée de 2,0 à 1,1.</span><span class="sxs-lookup"><span data-stu-id="83611-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="83611-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="83611-103">Version introduced</span></span>

<span data-ttu-id="83611-104">3.0</span><span class="sxs-lookup"><span data-stu-id="83611-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="83611-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="83611-105">Change description</span></span>

<span data-ttu-id="83611-106">Dans .NET Core 1.0 à 2.0, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> la valeur par défaut de la propriété est de 1,1.</span><span class="sxs-lookup"><span data-stu-id="83611-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="83611-107">À partir de .NET Core 2.1, il a été changé à 2,1.</span><span class="sxs-lookup"><span data-stu-id="83611-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="83611-108">À partir de .NET Core 3.0, <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> le numéro de version par défaut retourné par la propriété est une fois de plus 1,1.</span><span class="sxs-lookup"><span data-stu-id="83611-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="83611-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="83611-109">Recommended action</span></span>

<span data-ttu-id="83611-110">Mettez à jour votre <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> code si cela dépend de la propriété de retour d’une valeur par défaut de 2.0.</span><span class="sxs-lookup"><span data-stu-id="83611-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="83611-111">Category</span><span class="sxs-lookup"><span data-stu-id="83611-111">Category</span></span>

<span data-ttu-id="83611-112">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="83611-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="83611-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="83611-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-->
