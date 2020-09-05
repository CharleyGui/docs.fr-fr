---
ms.openlocfilehash: 25437dcc0c814ed2265b2efb34316af48b372ebd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496093"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="3e91c-101">Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs</span><span class="sxs-lookup"><span data-stu-id="3e91c-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="3e91c-102">Détails</span><span class="sxs-lookup"><span data-stu-id="3e91c-102">Details</span></span>

<span data-ttu-id="3e91c-103">Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place).</span><span class="sxs-lookup"><span data-stu-id="3e91c-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="3e91c-104">Ce problème est résolu depuis .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="3e91c-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3e91c-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="3e91c-105">Suggestion</span></span>

<span data-ttu-id="3e91c-106">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e91c-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="3e91c-107">Name</span><span class="sxs-lookup"><span data-stu-id="3e91c-107">Name</span></span>    | <span data-ttu-id="3e91c-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="3e91c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3e91c-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="3e91c-109">Scope</span></span>   |<span data-ttu-id="3e91c-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="3e91c-110">Minor</span></span>|
|<span data-ttu-id="3e91c-111">Version</span><span class="sxs-lookup"><span data-stu-id="3e91c-111">Version</span></span>|<span data-ttu-id="3e91c-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="3e91c-112">4.5.1</span></span>|
|<span data-ttu-id="3e91c-113">Type</span><span class="sxs-lookup"><span data-stu-id="3e91c-113">Type</span></span>|<span data-ttu-id="3e91c-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="3e91c-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="3e91c-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="3e91c-115">Affected APIs</span></span>

<span data-ttu-id="3e91c-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="3e91c-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
