---
ms.openlocfilehash: b50a108d2efbfd3da0d690cb02537a12f766b26b
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237343"
---
### <a name="default-value-of-httprequestmessageversion-changed-to-11"></a><span data-ttu-id="7ccb0-101">La valeur par défaut de HttpRequestMessage. version est passée à 1,1</span><span class="sxs-lookup"><span data-stu-id="7ccb0-101">Default value of HttpRequestMessage.Version changed to 1.1</span></span> 

<span data-ttu-id="7ccb0-102">La valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est passée de 2,0 à 1,1.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-102">The default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property has changed from 2.0 to 1.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7ccb0-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7ccb0-103">Version introduced</span></span>

<span data-ttu-id="7ccb0-104">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7ccb0-104">.NET Core 3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="7ccb0-105">Modifier la description</span><span class="sxs-lookup"><span data-stu-id="7ccb0-105">Change description</span></span>

<span data-ttu-id="7ccb0-106">Dans .NET Core 1,0 à 2,0, la valeur par défaut de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est 1,1.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-106">In .NET Core 1.0 through 2.0, the default value of the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is 1.1.</span></span> <span data-ttu-id="7ccb0-107">À compter de .NET Core 2,1, il a été remplacé par 2,1.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-107">Starting with .NET Core 2.1, it was changed to 2.1.</span></span> 

<span data-ttu-id="7ccb0-108">À compter de .NET Core 3,0, le numéro de version par défaut retourné par la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> est encore une fois 1,1.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-108">Starting with .NET Core 3.0, the default version number returned by the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property is once again 1.1.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="7ccb0-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7ccb0-109">Recommended action</span></span>

<span data-ttu-id="7ccb0-110">Mettez à jour votre code s’il dépend de la propriété <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> qui retourne une valeur par défaut de 2,0.</span><span class="sxs-lookup"><span data-stu-id="7ccb0-110">Update your code if it depends on the <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName> property returning a default value of 2.0.</span></span>

#### <a name="category"></a><span data-ttu-id="7ccb0-111">Catégorie</span><span class="sxs-lookup"><span data-stu-id="7ccb0-111">Category</span></span>

<span data-ttu-id="7ccb0-112">Réseau</span><span class="sxs-lookup"><span data-stu-id="7ccb0-112">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7ccb0-113">API affectées</span><span class="sxs-lookup"><span data-stu-id="7ccb0-113">Affected APIs</span></span>

- <xref:System.Net.Http.HttpRequestMessage.Version?displayProperty=fullName>

<!--
a def
### Affected APIs

- `P:System.Net.Http.HttpRequestMessage.Version`

-- >

