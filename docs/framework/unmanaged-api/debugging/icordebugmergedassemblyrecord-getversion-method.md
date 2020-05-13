---
title: ICorDebugMergedAssemblyRecord::GetVersion, méthode
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: cad71080c86e92beb318722db86011b09ce02e91
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207622"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a><span data-ttu-id="4497d-102">ICorDebugMergedAssemblyRecord::GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="4497d-102">ICorDebugMergedAssemblyRecord::GetVersion Method</span></span>
<span data-ttu-id="4497d-103">Obtient les informations de version de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="4497d-103">Gets the assembly's version information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4497d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4497d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4497d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4497d-105">Parameters</span></span>  
 `pMajor`  
 <span data-ttu-id="4497d-106">[out] Pointeur vers le numéro de version principale.</span><span class="sxs-lookup"><span data-stu-id="4497d-106">[out] A pointer to the major version number.</span></span>  
  
 `pMinor`  
 <span data-ttu-id="4497d-107">[out] Pointeur vers le numéro de version secondaire.</span><span class="sxs-lookup"><span data-stu-id="4497d-107">[out] A pointer to the minor version number.</span></span>  
  
 `pBuild`  
 <span data-ttu-id="4497d-108">[out] Pointeur vers le numéro de build.</span><span class="sxs-lookup"><span data-stu-id="4497d-108">[out] A pointer to the build number.</span></span>  
  
 `pRevision`  
 <span data-ttu-id="4497d-109">[out] Pointeur vers le numéro de révision.</span><span class="sxs-lookup"><span data-stu-id="4497d-109">[out] A pointer to the revision number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4497d-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="4497d-110">Remarks</span></span>  
 <span data-ttu-id="4497d-111">Pour plus d'informations sur les numéros de version d'assembly, consultez la rubrique de la classe <xref:System.Version>.</span><span class="sxs-lookup"><span data-stu-id="4497d-111">For information on assembly version numbers, see the <xref:System.Version> class topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4497d-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4497d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4497d-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4497d-113">Requirements</span></span>  
 <span data-ttu-id="4497d-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4497d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4497d-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4497d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4497d-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4497d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4497d-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4497d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4497d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4497d-118">See also</span></span>

- [<span data-ttu-id="4497d-119">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="4497d-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="4497d-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4497d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
