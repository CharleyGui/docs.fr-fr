---
title: ICorDebugMergedAssemblyRecord::GetPublicKey, méthode
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793115"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="7215f-102">ICorDebugMergedAssemblyRecord::GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="7215f-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="7215f-103">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="7215f-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7215f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7215f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7215f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7215f-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="7215f-106">[in] Nombre maximal d'octets dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="7215f-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="7215f-107">[out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="7215f-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="7215f-108">[in] Pointeur vers un tableau d'octets contenant la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="7215f-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7215f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="7215f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7215f-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7215f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7215f-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7215f-111">Requirements</span></span>  
 <span data-ttu-id="7215f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7215f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7215f-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7215f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7215f-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7215f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7215f-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7215f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7215f-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7215f-116">See also</span></span>

- [<span data-ttu-id="7215f-117">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="7215f-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="7215f-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7215f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
