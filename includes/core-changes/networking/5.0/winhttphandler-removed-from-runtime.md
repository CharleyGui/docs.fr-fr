---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608465"
---
### <a name="winhttphandler-removed-from-net-runtime"></a><span data-ttu-id="22a2c-101">WinHttpHandler supprimé du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="22a2c-101">WinHttpHandler removed from .NET runtime</span></span>

<span data-ttu-id="22a2c-102">La `WinHttpHandler` classe a été supprimée de l’assembly *System.Net.Http.dll* .</span><span class="sxs-lookup"><span data-stu-id="22a2c-102">The `WinHttpHandler` class was removed from the *System.Net.Http.dll* assembly.</span></span> <span data-ttu-id="22a2c-103">Il est désormais disponible uniquement en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)hors-bande (OOB).</span><span class="sxs-lookup"><span data-stu-id="22a2c-103">It's now available only as an out-of-band (OOB) [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22a2c-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="22a2c-104">Version introduced</span></span>

<span data-ttu-id="22a2c-105">5.0</span><span class="sxs-lookup"><span data-stu-id="22a2c-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="22a2c-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="22a2c-106">Change description</span></span>

<span data-ttu-id="22a2c-107">Dans les versions précédentes de .NET, la <xref:System.Net.Http.WinHttpHandler> classe est disponible dans le cadre des bibliothèques .net de base.</span><span class="sxs-lookup"><span data-stu-id="22a2c-107">In previous .NET versions, the <xref:System.Net.Http.WinHttpHandler> class is available as part of the core .NET libraries.</span></span> <span data-ttu-id="22a2c-108">À compter de .NET 5,0, la <xref:System.Net.Http.WinHttpHandler> classe est uniquement disponible en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)installé séparément.</span><span class="sxs-lookup"><span data-stu-id="22a2c-108">Starting in .NET 5.0, the <xref:System.Net.Http.WinHttpHandler> class is only available as a separately installed [NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22a2c-109">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="22a2c-109">Recommended action</span></span>

<span data-ttu-id="22a2c-110">Installez le [package NuGet System .net. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span><span class="sxs-lookup"><span data-stu-id="22a2c-110">Install the [System.Net.Http.WinHttpHandler NuGet package](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/).</span></span> <span data-ttu-id="22a2c-111">Ou, si vous n’avez pas besoin de fonctionnalités spécifiques à WinHTTP, utilisez à la <xref:System.Net.Http.SocketsHttpHandler> place.</span><span class="sxs-lookup"><span data-stu-id="22a2c-111">Or, if you don't require WinHTTP-specific features, use <xref:System.Net.Http.SocketsHttpHandler> instead.</span></span>

#### <a name="category"></a><span data-ttu-id="22a2c-112">Category</span><span class="sxs-lookup"><span data-stu-id="22a2c-112">Category</span></span>

<span data-ttu-id="22a2c-113">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="22a2c-113">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22a2c-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="22a2c-114">Affected APIs</span></span>

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
