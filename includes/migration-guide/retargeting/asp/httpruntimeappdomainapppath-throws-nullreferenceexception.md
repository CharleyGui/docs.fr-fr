---
ms.openlocfilehash: d6c658f306dd4792e3cb5dbdc9471043ca95a071
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859159"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a><span data-ttu-id="636c9-101">HttpRuntime.AppDomainAppPath lève une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="636c9-101">HttpRuntime.AppDomainAppPath Throws a NullReferenceException</span></span>

|   |   |
|---|---|
|<span data-ttu-id="636c9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="636c9-102">Details</span></span>|<span data-ttu-id="636c9-103">Dans .NET Framework 4.6.2, le runtime lève un <code>T:System.NullReferenceException</code> quand vous récupérez une valeur <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> qui inclut des caractères null. Dans .NET Framework 4.6.1 et les versions antérieures, le runtime lève un <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="636c9-103">In the .NET Framework 4.6.2, the runtime throws a <code>T:System.NullReferenceException</code> when retrieving a <code>P:System.Web.HttpRuntime.AppDomainAppPath</code> value that includes null characters.In the .NET Framework 4.6.1 and earlier versions, the runtime throws an <code>T:System.ArgumentNullException</code>.</span></span>|
|<span data-ttu-id="636c9-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="636c9-104">Suggestion</span></span>|<span data-ttu-id="636c9-105">Vous pouvez effectuer l’une ou l’autre des opérations suivantes pour répondre à ce changement :</span><span class="sxs-lookup"><span data-stu-id="636c9-105">You can do either of the follow to respond to this change:</span></span><ul><li><span data-ttu-id="636c9-106">Gérer <code>T:System.NullReferenceException</code> si votre application s’exécute sur .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="636c9-106">Handle the <code>T:System.NullReferenceException</code> if you application is running on the .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="636c9-107">Effectuer une mise à niveau vers .NET Framework 4.7, qui restaure le comportement précédent et lève un <code>T:System.ArgumentNullException</code>.</span><span class="sxs-lookup"><span data-stu-id="636c9-107">Upgrade to the .NET Framework 4.7, which restores the previous behavior and throws an <code>T:System.ArgumentNullException</code>.</span></span></li></ul>|
|<span data-ttu-id="636c9-108">Portée</span><span class="sxs-lookup"><span data-stu-id="636c9-108">Scope</span></span>|<span data-ttu-id="636c9-109">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="636c9-109">Edge</span></span>|
|<span data-ttu-id="636c9-110">Version</span><span class="sxs-lookup"><span data-stu-id="636c9-110">Version</span></span>|<span data-ttu-id="636c9-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="636c9-111">4.6.2</span></span>|
|<span data-ttu-id="636c9-112">Type</span><span class="sxs-lookup"><span data-stu-id="636c9-112">Type</span></span>|<span data-ttu-id="636c9-113">Reciblage</span><span class="sxs-lookup"><span data-stu-id="636c9-113">Retargeting</span></span>|
|<span data-ttu-id="636c9-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="636c9-114">Affected APIs</span></span>|<ul><li><xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType></li></ul>|

