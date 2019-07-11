---
title: ICorDebugDataTarget2::GetImageFromPointer, méthode
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5656bf28d92030ed8d8271d795e41f881932a73
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750212"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="7c20e-102">ICorDebugDataTarget2::GetImageFromPointer, méthode</span><span class="sxs-lookup"><span data-stu-id="7c20e-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="7c20e-103">Retourne l'adresse de base et la taille d'un module à partir d'une adresse présente dans ce module.</span><span class="sxs-lookup"><span data-stu-id="7c20e-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c20e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c20e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c20e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c20e-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="7c20e-106">Un [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valeur qui représente une adresse dans un module.</span><span class="sxs-lookup"><span data-stu-id="7c20e-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="7c20e-107">[out] Un [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valeur qui représente l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="7c20e-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="7c20e-108">Pointeur vers la taille du module.</span><span class="sxs-lookup"><span data-stu-id="7c20e-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c20e-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7c20e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c20e-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7c20e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c20e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7c20e-111">Requirements</span></span>  
 <span data-ttu-id="7c20e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c20e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c20e-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c20e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c20e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c20e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c20e-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c20e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c20e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c20e-116">See also</span></span>

- [<span data-ttu-id="7c20e-117">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="7c20e-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="7c20e-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7c20e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
