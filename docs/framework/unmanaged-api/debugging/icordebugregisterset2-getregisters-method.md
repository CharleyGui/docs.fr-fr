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
ms.openlocfilehash: b7a356d80d63fae65191bbf4fc0a23d7e02004c9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378229"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="a794f-102">ICorDebugRegisterSet2::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="a794f-102">ICorDebugRegisterSet2::GetRegisters Method</span></span>
<span data-ttu-id="a794f-103">Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) spécifié par le masque de bits donné.</span><span class="sxs-lookup"><span data-stu-id="a794f-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a794f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a794f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a794f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a794f-105">Parameters</span></span>  
 `maskCount`  
 <span data-ttu-id="a794f-106">dans Taille, en octets, du `mask` tableau.</span><span class="sxs-lookup"><span data-stu-id="a794f-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="a794f-107">dans Tableau d’octets, chacun d’eux correspondant à un registre.</span><span class="sxs-lookup"><span data-stu-id="a794f-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="a794f-108">Si le bit est 1, la valeur du Registre correspondant est récupérée.</span><span class="sxs-lookup"><span data-stu-id="a794f-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="a794f-109">dans Nombre de valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="a794f-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="a794f-110">à Tableau d' `CORDB_REGISTER` objets, chacun d’entre eux recevant la valeur d’un registre.</span><span class="sxs-lookup"><span data-stu-id="a794f-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a794f-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a794f-111">Remarks</span></span>  
 <span data-ttu-id="a794f-112">La `GetRegisters` méthode retourne un tableau de valeurs à partir des registres spécifiés par le masque.</span><span class="sxs-lookup"><span data-stu-id="a794f-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="a794f-113">Le tableau ne contient pas de valeurs de registres dont le bit de masque n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="a794f-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="a794f-114">Par conséquent, la taille du `regBuffer` tableau doit être égale au nombre de 1 dans le masque.</span><span class="sxs-lookup"><span data-stu-id="a794f-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="a794f-115">Si la valeur de `regCount` est trop petite pour le nombre de registres indiqué par le masque, les valeurs des registres numérotés les plus élevés seront tronquées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="a794f-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="a794f-116">Si `regCount` est trop grand, les éléments inutilisés `regBuffer` ne seront pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="a794f-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="a794f-117">Si un registre non disponible est indiqué par le masque, une valeur indéterminée est retournée pour ce registre.</span><span class="sxs-lookup"><span data-stu-id="a794f-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="a794f-118">La `ICorDebugRegisterSet2::GetRegisters` méthode est nécessaire pour les plateformes qui ont plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="a794f-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms which have more than 64 registers.</span></span> <span data-ttu-id="a794f-119">Par exemple, IA64 a des registres à usage général 128 et des registres à virgule flottante 128. vous avez donc besoin de plus de 64 bits dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="a794f-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64-bits in the bit mask.</span></span>  
  
 <span data-ttu-id="a794f-120">Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes telles que x86, la `GetRegisters` méthode convertit en fait simplement les octets du `mask` tableau d’octets en un `ULONG64` , puis appelle la méthode [ICorDebugRegisterSet :: GetRegisters,](icordebugregisterset-getregisters-method.md) , qui prend le `ULONG64` masque.</span><span class="sxs-lookup"><span data-stu-id="a794f-120">If you do not have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method actually just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a794f-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a794f-121">Requirements</span></span>  
 <span data-ttu-id="a794f-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a794f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a794f-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a794f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a794f-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a794f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a794f-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a794f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a794f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a794f-126">See also</span></span>

- [<span data-ttu-id="a794f-127">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="a794f-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="a794f-128">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="a794f-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
