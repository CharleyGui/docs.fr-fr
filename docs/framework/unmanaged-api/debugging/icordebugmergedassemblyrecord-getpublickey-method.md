---
title: 'ICorDebugMergedAssemblyRecord :: GetPublicKey,, méthode'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 9cf5f6b6d12303b3f59588c5fb663c457da79cb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131394"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="8d2c3-102">ICorDebugMergedAssemblyRecord :: GetPublicKey,, méthode</span><span class="sxs-lookup"><span data-stu-id="8d2c3-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="8d2c3-103">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d2c3-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d2c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d2c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d2c3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d2c3-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="8d2c3-106">[in] Nombre maximal d'octets dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="8d2c3-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="8d2c3-107">[out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="8d2c3-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="8d2c3-108">[in] Pointeur vers un tableau d'octets contenant la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="8d2c3-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d2c3-109">Notes</span><span class="sxs-lookup"><span data-stu-id="8d2c3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d2c3-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d2c3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d2c3-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="8d2c3-111">Requirements</span></span>  
 <span data-ttu-id="8d2c3-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d2c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d2c3-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d2c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d2c3-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d2c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d2c3-115">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d2c3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d2c3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d2c3-116">See also</span></span>

- [<span data-ttu-id="8d2c3-117">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="8d2c3-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="8d2c3-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8d2c3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
