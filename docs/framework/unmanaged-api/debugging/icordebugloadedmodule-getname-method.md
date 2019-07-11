---
title: ICorDebugLoadedModule::GetName (méthode)
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b3889829ced876b23ea6632f35f4da6beffdca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759925"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="898f3-102">ICorDebugLoadedModule::GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="898f3-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="898f3-103">Obtient le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="898f3-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="898f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="898f3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="898f3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="898f3-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="898f3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="898f3-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="898f3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="898f3-108">[out] Tableau de caractères contenant le nom du module chargé.</span><span class="sxs-lookup"><span data-stu-id="898f3-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="898f3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="898f3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="898f3-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="898f3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="898f3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="898f3-111">Requirements</span></span>  
 <span data-ttu-id="898f3-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="898f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="898f3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="898f3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="898f3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="898f3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="898f3-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="898f3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898f3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="898f3-116">See also</span></span>

- [<span data-ttu-id="898f3-117">ICorDebugLoadedModule, interface</span><span class="sxs-lookup"><span data-stu-id="898f3-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="898f3-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="898f3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
