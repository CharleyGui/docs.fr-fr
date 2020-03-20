---
ms.openlocfilehash: e7154919d6a09a04e650d5546feb2ae6c6cc912f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859159"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="13e25-101">HttpRuntime.AppDomainAppPath lève une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="13e25-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="13e25-102">Détails</span><span class="sxs-lookup"><span data-stu-id="13e25-102">Details</span></span>|<span data-ttu-id="13e25-103">Dans .NET Framework 4.6.2, le runtime lève un <code>T:System.NullReferenceException</code> quand vous récupérez une valeur <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> qui inclut des caractères null. Dans .NET Framework 4.6.1 et les versions antérieures, le runtime lève un <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="13e25-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="13e25-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="13e25-104">Suggestion</span></span>|<span data-ttu-id="13e25-105">Vous pouvez effectuer l’une ou l’autre des opérations suivantes pour répondre à ce changement :</span><span class="sxs-lookup"><span data-stu-id="13e25-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="13e25-106">Gérer <code>T:System.NullReferenceException</code> si votre application s’exécute sur .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="13e25-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="13e25-107">Effectuer une mise à niveau vers .NET Framework 4.7, qui restaure le comportement précédent et lève un <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="13e25-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="13e25-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="13e25-108">Scope</span></span>|<span data-ttu-id="13e25-109">Edge</span><span class="sxs-lookup"><span data-stu-id="13e25-109">Edge</span></span>|
|<span data-ttu-id="13e25-110">Version</span><span class="sxs-lookup"><span data-stu-id="13e25-110">Version</span></span>|<span data-ttu-id="13e25-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="13e25-111">4.6.2</span></span>|
|<span data-ttu-id="13e25-112">Type</span><span class="sxs-lookup"><span data-stu-id="13e25-112">Type</span></span>|<span data-ttu-id="13e25-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="13e25-113">Retargeting</span></span>|
|<span data-ttu-id="13e25-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="13e25-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|
