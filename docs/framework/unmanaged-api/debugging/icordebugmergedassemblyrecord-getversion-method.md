---
title: ICorDebugMergedAssemblyRecord::GetVersion, méthode
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178686"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="363af-102">ICorDebugMergedAssemblyRecord::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="363af-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="363af-103">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="363af-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="363af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="363af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="363af-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="363af-106">[out] Pointeur vers le numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="363af-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="363af-107">[out] Pointeur vers le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="363af-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="363af-108">[out] Pointeur vers le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="363af-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="363af-109">[out] Pointeur vers le numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="363af-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="363af-110">Notes </span><span class="sxs-lookup"><span data-stu-id="363af-110">Remarks</span></span>  
 <span data-ttu-id="363af-111">Pour plus d'informations sur les numéros de version d'assembly, consultez la rubrique de la classe <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="363af-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="363af-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="363af-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363af-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="363af-113">Requirements</span></span>  
 <span data-ttu-id="363af-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="363af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363af-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="363af-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="363af-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="363af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="363af-117">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363af-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363af-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="363af-118">See also</span></span>

- [<span data-ttu-id="363af-119">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="363af-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="363af-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="363af-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
