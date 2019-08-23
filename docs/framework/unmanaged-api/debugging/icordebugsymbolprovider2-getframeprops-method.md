---
title: Méthode ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c22e9c58a203c13611298e1956a6951d8ca7e8b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955496"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="926c6-102">Méthode ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="926c6-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="926c6-103">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="926c6-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="926c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="926c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="926c6-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="926c6-106">[in] Adresse virtuelle relative du code.</span><span class="sxs-lookup"><span data-stu-id="926c6-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="926c6-107">[out] Pointeur vers l'adresse virtuelle relative de départ de la méthode.</span><span class="sxs-lookup"><span data-stu-id="926c6-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="926c6-108">[out] Pointeur vers l'adresse virtuelle relative de départ du frame.</span><span class="sxs-lookup"><span data-stu-id="926c6-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="926c6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="926c6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="926c6-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="926c6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926c6-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="926c6-111">Requirements</span></span>  
 <span data-ttu-id="926c6-112">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="926c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="926c6-113">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="926c6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="926c6-114">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="926c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="926c6-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="926c6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926c6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="926c6-116">See also</span></span>

- [<span data-ttu-id="926c6-117">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="926c6-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="926c6-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="926c6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
