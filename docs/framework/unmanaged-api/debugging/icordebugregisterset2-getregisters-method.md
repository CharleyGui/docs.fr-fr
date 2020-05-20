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
ms.openlocfilehash: 71b9d59621efb547713cb4a6c9df7a7142f4a677
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615187"
---
# <a name="icordebugregisterset2getregisters-method"></a><span data-ttu-id="116d0-102">ICorDebugRegisterSet2 :: GetRegisters,, méthode</span><span class="sxs-lookup"><span data-stu-id="116d0-102">ICorDebugRegisterSet2::GetRegisters method</span></span>

<span data-ttu-id="116d0-103">Obtient la valeur de chaque registre (pour la plateforme sur laquelle le code est en cours d’exécution) spécifié par le masque de bits donné.</span><span class="sxs-lookup"><span data-stu-id="116d0-103">Gets the value of each register (for the platform on which code is currently executing) that is specified by the given bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="116d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="116d0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [out, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="116d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="116d0-105">Parameters</span></span>

 `maskCount`  
 <span data-ttu-id="116d0-106">dans Taille, en octets, du `mask` tableau.</span><span class="sxs-lookup"><span data-stu-id="116d0-106">[in] The size, in bytes, of the `mask` array.</span></span>  
  
 `mask`  
 <span data-ttu-id="116d0-107">dans Tableau d’octets, chacun d’eux correspondant à un registre.</span><span class="sxs-lookup"><span data-stu-id="116d0-107">[in] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="116d0-108">Si le bit est 1, la valeur du Registre correspondant est récupérée.</span><span class="sxs-lookup"><span data-stu-id="116d0-108">If the bit is 1, the corresponding register's value will be retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="116d0-109">dans Nombre de valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="116d0-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="116d0-110">à Tableau d' `CORDB_REGISTER` objets, chacun d’entre eux recevant la valeur d’un registre.</span><span class="sxs-lookup"><span data-stu-id="116d0-110">[out] An array of `CORDB_REGISTER` objects, each of which receives the value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="116d0-111">Notes</span><span class="sxs-lookup"><span data-stu-id="116d0-111">Remarks</span></span>

 <span data-ttu-id="116d0-112">La `GetRegisters` méthode retourne un tableau de valeurs à partir des registres spécifiés par le masque.</span><span class="sxs-lookup"><span data-stu-id="116d0-112">The `GetRegisters` method returns an array of values from the registers that are specified by the mask.</span></span> <span data-ttu-id="116d0-113">Le tableau ne contient pas de valeurs de registres dont le bit de masque n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="116d0-113">The array does not contain values of registers whose mask bit is not set.</span></span> <span data-ttu-id="116d0-114">Par conséquent, la taille du `regBuffer` tableau doit être égale au nombre de 1 dans le masque.</span><span class="sxs-lookup"><span data-stu-id="116d0-114">Thus, the size of the `regBuffer` array must be equal to the number of 1's in the mask.</span></span> <span data-ttu-id="116d0-115">Si la valeur de `regCount` est trop petite pour le nombre de registres indiqué par le masque, les valeurs des registres numérotés les plus élevés seront tronquées de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="116d0-115">If the value of `regCount` is too small for the number of registers indicated by the mask, the values of the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="116d0-116">Si `regCount` est trop grand, les éléments inutilisés `regBuffer` ne seront pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="116d0-116">If `regCount` is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="116d0-117">Si un registre non disponible est indiqué par le masque, une valeur indéterminée est retournée pour ce registre.</span><span class="sxs-lookup"><span data-stu-id="116d0-117">If an unavailable register is indicated by the mask, an indeterminate value will be returned for that register.</span></span>  
  
 <span data-ttu-id="116d0-118">La `ICorDebugRegisterSet2::GetRegisters` méthode est nécessaire pour les plateformes qui ont plus de 64 registres.</span><span class="sxs-lookup"><span data-stu-id="116d0-118">The `ICorDebugRegisterSet2::GetRegisters` method is necessary for platforms that have more than 64 registers.</span></span> <span data-ttu-id="116d0-119">Par exemple, IA64 a des registres à usage général 128 et des registres à virgule flottante 128. vous avez donc besoin de plus de 64 bits dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="116d0-119">For example, IA64 has 128 general purpose registers and 128 floating-point registers, so you need more than 64 bits in the bit mask.</span></span>  
  
 <span data-ttu-id="116d0-120">Si vous n’avez pas plus de 64 registres, comme c’est le cas sur les plateformes telles que x86, la `GetRegisters` méthode convertit simplement les octets du `mask` tableau d’octets en un `ULONG64` , puis appelle la méthode [ICorDebugRegisterSet :: GetRegisters,](icordebugregisterset-getregisters-method.md) , qui prend le `ULONG64` masque.</span><span class="sxs-lookup"><span data-stu-id="116d0-120">If you don't have more than 64 registers, as is the case on platforms such as x86, the `GetRegisters` method just translates the bytes in the `mask` byte array into a `ULONG64` and then calls the [ICorDebugRegisterSet::GetRegisters](icordebugregisterset-getregisters-method.md) method, which takes the `ULONG64` mask.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="116d0-121">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="116d0-121">Requirements</span></span>

 <span data-ttu-id="116d0-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="116d0-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="116d0-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="116d0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="116d0-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="116d0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="116d0-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="116d0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="116d0-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="116d0-126">See also</span></span>

- [<span data-ttu-id="116d0-127">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="116d0-127">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="116d0-128">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="116d0-128">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
