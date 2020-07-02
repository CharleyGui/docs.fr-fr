---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619956"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="f8e52-101">Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs</span><span class="sxs-lookup"><span data-stu-id="f8e52-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="f8e52-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f8e52-102">Details</span></span>

<span data-ttu-id="f8e52-103">Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place).</span><span class="sxs-lookup"><span data-stu-id="f8e52-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="f8e52-104">Ce problème est résolu depuis .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="f8e52-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f8e52-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f8e52-105">Suggestion</span></span>

<span data-ttu-id="f8e52-106">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8e52-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="f8e52-107">Nom</span><span class="sxs-lookup"><span data-stu-id="f8e52-107">Name</span></span>    | <span data-ttu-id="f8e52-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="f8e52-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f8e52-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="f8e52-109">Scope</span></span>   |<span data-ttu-id="f8e52-110">Secondaire</span><span class="sxs-lookup"><span data-stu-id="f8e52-110">Minor</span></span>|
|<span data-ttu-id="f8e52-111">Version</span><span class="sxs-lookup"><span data-stu-id="f8e52-111">Version</span></span>|<span data-ttu-id="f8e52-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f8e52-112">4.5.1</span></span>|
|<span data-ttu-id="f8e52-113">Type</span><span class="sxs-lookup"><span data-stu-id="f8e52-113">Type</span></span>|<span data-ttu-id="f8e52-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="f8e52-114">Runtime</span></span>|
