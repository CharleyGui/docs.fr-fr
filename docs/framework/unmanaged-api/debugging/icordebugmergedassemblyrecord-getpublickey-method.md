---
title: ICorDebugMergedAssemblyRecord::GetPublicKey, méthode
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 51724aa1ee6101c50c7cdb4b6071fb458814f483
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213541"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="23fdf-102">ICorDebugMergedAssemblyRecord::GetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="23fdf-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="23fdf-103">Obtient la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="23fdf-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23fdf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23fdf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23fdf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23fdf-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="23fdf-106">[in] Nombre maximal d'octets dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="23fdf-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="23fdf-107">[out] Pointeur vers le nombre réel d'octets écrits dans le tableau `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="23fdf-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="23fdf-108">[in] Pointeur vers un tableau d'octets contenant la clé publique de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="23fdf-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23fdf-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="23fdf-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23fdf-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="23fdf-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23fdf-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="23fdf-111">Requirements</span></span>  
 <span data-ttu-id="23fdf-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23fdf-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23fdf-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23fdf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23fdf-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23fdf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23fdf-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23fdf-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23fdf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23fdf-116">See also</span></span>

- [<span data-ttu-id="23fdf-117">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="23fdf-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="23fdf-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="23fdf-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
