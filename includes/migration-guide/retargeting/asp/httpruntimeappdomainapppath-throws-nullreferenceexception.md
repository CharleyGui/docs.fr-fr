---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617529"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="acab2-101">HttpRuntime.AppDomainAppPath lève une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="acab2-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="acab2-102">Détails</span><span class="sxs-lookup"><span data-stu-id="acab2-102">Details</span></span>

<span data-ttu-id="acab2-103">Dans .NET Framework 4.6.2, le runtime lève un `T:System.NullReferenceException` quand vous récupérez une valeur `P:System.Web.HttpRuntime.AppDomainAppPath` qui inclut des caractères null. Dans .NET Framework 4.6.1 et les versions antérieures, le runtime lève un `T:System.ArgumentNullException`.</span><span class="sxs-lookup"><span data-stu-id="acab2-103">In the .NET Framework 4.6.2, the runtime throws a `T:System.NullReferenceException` when retrieving a `P:System.Web.HttpRuntime.AppDomainAppPath` value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an `T:System.ArgumentNullException`.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="acab2-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="acab2-104">Suggestion</span></span>

<span data-ttu-id="acab2-105">Vous pouvez effectuer l’une ou l’autre des opérations suivantes pour répondre à ce changement :</span><span class="sxs-lookup"><span data-stu-id="acab2-105">You can do either of the follow to respond to this change:</span></span>

- <span data-ttu-id="acab2-106">Gérer `T:System.NullReferenceException` si votre application s’exécute sur .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="acab2-106">Handle the `T:System.NullReferenceException` if you application is running on the .NET Framework 4.6.2.</span></span>
- <span data-ttu-id="acab2-107">Effectuer une mise à niveau vers .NET Framework 4.7, qui restaure le comportement précédent et lève un `T:System.ArgumentNullException`.</span><span class="sxs-lookup"><span data-stu-id="acab2-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an `T:System.ArgumentNullException`.</span></span>

| <span data-ttu-id="acab2-108">Nom</span><span class="sxs-lookup"><span data-stu-id="acab2-108">Name</span></span>    | <span data-ttu-id="acab2-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="acab2-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="acab2-110">Étendue</span><span class="sxs-lookup"><span data-stu-id="acab2-110">Scope</span></span>   | <span data-ttu-id="acab2-111">Edge</span><span class="sxs-lookup"><span data-stu-id="acab2-111">Edge</span></span>        |
| <span data-ttu-id="acab2-112">Version</span><span class="sxs-lookup"><span data-stu-id="acab2-112">Version</span></span> | <span data-ttu-id="acab2-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="acab2-113">4.6.2</span></span>       |
| <span data-ttu-id="acab2-114">Type</span><span class="sxs-lookup"><span data-stu-id="acab2-114">Type</span></span>    | <span data-ttu-id="acab2-115">Reciblage</span><span class="sxs-lookup"><span data-stu-id="acab2-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="acab2-116">API affectées</span><span class="sxs-lookup"><span data-stu-id="acab2-116">Affected APIs</span></span>

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
