---
title: ICorDebugMergedAssemblyRecord::GetVersion, méthode
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 8b5995183be7f1c992cf3230e16456cb248eff0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793077"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="9a812-102">ICorDebugMergedAssemblyRecord::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="9a812-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="9a812-103">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9a812-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a812-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a812-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,   
   [out] USHORT *pMinor,   
   [out] USHORT *pBuild,   
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a812-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="9a812-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="9a812-106">[out] Pointeur vers le numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="9a812-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="9a812-107">[out] Pointeur vers le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="9a812-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="9a812-108">[out] Pointeur vers le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="9a812-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="9a812-109">[out] Pointeur vers le numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="9a812-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a812-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9a812-110">Remarks</span></span>  
 <span data-ttu-id="9a812-111">Pour plus d'informations sur les numéros de version d'assembly, consultez la rubrique de la classe <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="9a812-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a812-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9a812-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a812-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="9a812-113">Requirements</span></span>  
 <span data-ttu-id="9a812-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a812-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a812-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a812-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a812-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a812-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a812-117">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a812-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a812-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a812-118">See also</span></span>

- [<span data-ttu-id="9a812-119">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="9a812-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="9a812-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9a812-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
