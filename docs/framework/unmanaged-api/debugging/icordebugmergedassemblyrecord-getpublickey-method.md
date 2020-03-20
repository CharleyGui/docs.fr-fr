---
title: ICorDebugMergedAssemblyRecord::GetPublicKey, méthode
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178741"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="286b2-102">ICorDebugMergedAssemblyRecord::GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="286b2-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="286b2-103">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="286b2-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="286b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="286b2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="286b2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="286b2-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="286b2-106">[in] Nombre maximal d'octets dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="286b2-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="286b2-107">[out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="286b2-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="286b2-108">[in] Pointeur vers un tableau d'octets contenant la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="286b2-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="286b2-109">Notes </span><span class="sxs-lookup"><span data-stu-id="286b2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="286b2-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="286b2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="286b2-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="286b2-111">Requirements</span></span>  
 <span data-ttu-id="286b2-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="286b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="286b2-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="286b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="286b2-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="286b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="286b2-115">**.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="286b2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286b2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="286b2-116">See also</span></span>

- [<span data-ttu-id="286b2-117">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="286b2-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="286b2-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="286b2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
