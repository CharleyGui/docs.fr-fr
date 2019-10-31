---
ms.openlocfilehash: ff156afb3da4b921517fd841c5de2295265a8d7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198413"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="33a66-101">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="33a66-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span>

<span data-ttu-id="33a66-102">La valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est passée de 2,0 à 1,1.</span><span class="sxs-lookup"><span data-stu-id="33a66-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="33a66-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="33a66-103">Version introduced</span></span>

<span data-ttu-id="33a66-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="33a66-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="33a66-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="33a66-105">Change description</span></span>

<span data-ttu-id="33a66-106">Dans .NET Core 1,0 à 2,0, la valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est 1,1.</span><span class="sxs-lookup"><span data-stu-id="33a66-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="33a66-107">À compter de .NET Core 2,1, il a été remplacé par 2,1.</span><span class="sxs-lookup"><span data-stu-id="33a66-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span>

<span data-ttu-id="33a66-108">À compter de .NET Core 3,0, le numéro de version par défaut retourné par la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est encore une fois 1,1.</span><span class="sxs-lookup"><span data-stu-id="33a66-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="33a66-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="33a66-109">Recommended action</span></span>

<span data-ttu-id="33a66-110">Mettez à jour votre code s’il dépend de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> retournant une valeur par défaut de 2,0.</span><span class="sxs-lookup"><span data-stu-id="33a66-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="33a66-111">Category</span><span class="sxs-lookup"><span data-stu-id="33a66-111">Category</span></span>

<span data-ttu-id="33a66-112">Réseau</span><span class="sxs-lookup"><span data-stu-id="33a66-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="33a66-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="33a66-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

