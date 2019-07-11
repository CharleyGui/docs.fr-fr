---
title: ICorDebugRegisterSet2::GetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegisters method [.NET Framework debugging]
ms.assetid: dbc498a8-ba3f-42f2-bdd9-b623c77a1019
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3c1b90390689e709ee131935bd6417fa6b273eb2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769985"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="2fb94-102">ICorDebugRegisterSet2::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="2fb94-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="2fb94-103">Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) qui est spécifié par le masque de bits donné.</span><span class="sxs-lookup"><span data-stu-id="2fb94-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2fb94-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fb94-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2fb94-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="2fb94-106">[in] La taille, en octets, de la `mask` tableau.</span><span class="sxs-lookup"><span data-stu-id="2fb94-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="2fb94-107">[in] Tableau d’octets, dont chaque bit correspond à un Registre.</span><span class="sxs-lookup"><span data-stu-id="2fb94-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="2fb94-108">Si le bit est 1, valeur de Registre correspondantes est récupérée.</span><span class="sxs-lookup"><span data-stu-id="2fb94-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="2fb94-109">[in] Le nombre de valeurs de registres à récupérer.</span><span class="sxs-lookup"><span data-stu-id="2fb94-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="2fb94-110">[out] Un tableau de `CORDB_REGISTER` objets, chacun d'entre eux reçoit la valeur d’un Registre.</span><span class="sxs-lookup"><span data-stu-id="2fb94-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb94-111">Notes</span><span class="sxs-lookup"><span data-stu-id="2fb94-111">Remarks</span></span>  
 <span data-ttu-id="2fb94-112">Le `GetRegisters` méthode retourne un tableau de valeurs à partir des registres qui sont spécifiés par le masque.</span><span class="sxs-lookup"><span data-stu-id="2fb94-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="2fb94-113">Le tableau ne contient pas les valeurs des registres dont le bit masque n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="2fb94-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="2fb94-114">Par conséquent, la taille de la `regBuffer` tableau doit être égal au nombre de 1 dans le masque.</span><span class="sxs-lookup"><span data-stu-id="2fb94-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="2fb94-115">Si la valeur de `regCount` est trop petite pour le nombre de registres indiqué par le masque, les valeurs les plus élevées des registres est tronqué de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="2fb94-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="2fb94-116">Si `regCount` est trop volumineux, l’inutilisé `regBuffer` éléments ne sont pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="2fb94-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="2fb94-117">Si un Registre non disponible est indiqué par le masque, une valeur indéterminée s’affichera pour ce Registre.</span><span class="sxs-lookup"><span data-stu-id="2fb94-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="2fb94-118">Le `ICorDebugRegisterSet2::GetRegisters` méthode est nécessaire pour les plateformes qui ont plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="2fb94-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="2fb94-119">Par exemple, IA64 comporte 128 registres à usage général et 128 registres en virgule flottante, et vous devez donc plus de 64 bits dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="2fb94-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="2fb94-120">Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes, telles que x86, le `GetRegisters` méthode traduit en fait juste les octets dans le `mask` tableau d’octets dans un `ULONG64` , puis appelle le [ICorDebugRegisterSet :: GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) (méthode), qui prend le `ULONG64` masque.</span><span class="sxs-lookup"><span data-stu-id="2fb94-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb94-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2fb94-121">Requirements</span></span>  
 <span data-ttu-id="2fb94-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb94-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb94-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fb94-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fb94-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fb94-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fb94-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb94-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb94-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2fb94-126">See also</span></span>

- [<span data-ttu-id="2fb94-127">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="2fb94-127">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="2fb94-128">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="2fb94-128">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
