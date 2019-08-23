---
title: ICorDebugLoadedModule::GetName (méthode)
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63341bcd6079688ed1a8e18ec8c422bca1427c72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910080"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="9a29f-102">ICorDebugLoadedModule::GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="9a29f-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="9a29f-103">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="9a29f-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a29f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a29f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a29f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a29f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9a29f-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="9a29f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9a29f-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="9a29f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a29f-108">[out] Tableau de caractères contenant le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="9a29f-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a29f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9a29f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a29f-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9a29f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a29f-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9a29f-111">Requirements</span></span>  
 <span data-ttu-id="9a29f-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a29f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a29f-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a29f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a29f-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a29f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a29f-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a29f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a29f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a29f-116">See also</span></span>

- [<span data-ttu-id="9a29f-117">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="9a29f-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="9a29f-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9a29f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
