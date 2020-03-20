---
title: ICorDebugDataTarget2::GetImageFromPointer, méthode
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178918"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="c8b2f-102">ICorDebugDataTarget2::GetImageFromPointer, méthode</span><span class="sxs-lookup"><span data-stu-id="c8b2f-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="c8b2f-103">Retourne l'adresse de base et la taille d'un module à partir d'une adresse présente dans ce module.</span><span class="sxs-lookup"><span data-stu-id="c8b2f-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8b2f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b2f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8b2f-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="c8b2f-106">Une [valeur CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente une adresse dans un module.</span><span class="sxs-lookup"><span data-stu-id="c8b2f-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="c8b2f-107">[out] Une [valeur CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) qui représente l’adresse de base du module.</span><span class="sxs-lookup"><span data-stu-id="c8b2f-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="c8b2f-108">Pointeur vers la taille du module.</span><span class="sxs-lookup"><span data-stu-id="c8b2f-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8b2f-109">Notes </span><span class="sxs-lookup"><span data-stu-id="c8b2f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8b2f-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c8b2f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b2f-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c8b2f-111">Requirements</span></span>  
 <span data-ttu-id="c8b2f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8b2f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b2f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8b2f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8b2f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b2f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8b2f-115">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b2f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b2f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8b2f-116">See also</span></span>

- [<span data-ttu-id="c8b2f-117">ICorDebugDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="c8b2f-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="c8b2f-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c8b2f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
