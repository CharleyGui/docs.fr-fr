---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858574"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="09084-101">Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs</span><span class="sxs-lookup"><span data-stu-id="09084-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="09084-102">Détails</span><span class="sxs-lookup"><span data-stu-id="09084-102">Details</span></span>|<span data-ttu-id="09084-103">Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place).</span><span class="sxs-lookup"><span data-stu-id="09084-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="09084-104">Ce problème est résolu depuis .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="09084-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="09084-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="09084-105">Suggestion</span></span>|<span data-ttu-id="09084-106">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="09084-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="09084-107">Étendue</span><span class="sxs-lookup"><span data-stu-id="09084-107">Scope</span></span>|<span data-ttu-id="09084-108">Secondaire</span><span class="sxs-lookup"><span data-stu-id="09084-108">Minor</span></span>|
|<span data-ttu-id="09084-109">Version</span><span class="sxs-lookup"><span data-stu-id="09084-109">Version</span></span>|<span data-ttu-id="09084-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="09084-110">4.5.1</span></span>|
|<span data-ttu-id="09084-111">Type</span><span class="sxs-lookup"><span data-stu-id="09084-111">Type</span></span>|<span data-ttu-id="09084-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="09084-112">Runtime</span></span>|
