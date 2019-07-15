---
ms.openlocfilehash: 8dc98b2d9c2c0b5f145ebce48cf8f5e054975c6e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858574"
---
### <a name="corprfgcroothandles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="062ec-101">Les membres COR_PRF_GC_ROOT_HANDLE ne sont pas énumérés par les profileurs</span><span class="sxs-lookup"><span data-stu-id="062ec-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="062ec-102">Détails</span><span class="sxs-lookup"><span data-stu-id="062ec-102">Details</span></span>|<span data-ttu-id="062ec-103">Dans .NET Framework 4.5.1, l’API de profilage <code>RootReferences2()</code> ne retourne jamais correctement <code>COR_PRF_GC_ROOT_HANDLE</code> (ils sont retournés comme <code>COR_PRF_GC_ROOT_OTHER</code> à la place).</span><span class="sxs-lookup"><span data-stu-id="062ec-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="062ec-104">Ce problème est résolu depuis .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="062ec-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="062ec-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="062ec-105">Suggestion</span></span>|<span data-ttu-id="062ec-106">Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant une mise à niveau vers cette version du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="062ec-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="062ec-107">Portée</span><span class="sxs-lookup"><span data-stu-id="062ec-107">Scope</span></span>|<span data-ttu-id="062ec-108">Mineur</span><span class="sxs-lookup"><span data-stu-id="062ec-108">Minor</span></span>|
|<span data-ttu-id="062ec-109">Version</span><span class="sxs-lookup"><span data-stu-id="062ec-109">Version</span></span>|<span data-ttu-id="062ec-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="062ec-110">4.5.1</span></span>|
|<span data-ttu-id="062ec-111">Type</span><span class="sxs-lookup"><span data-stu-id="062ec-111">Type</span></span>|<span data-ttu-id="062ec-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="062ec-112">Runtime</span></span>|

