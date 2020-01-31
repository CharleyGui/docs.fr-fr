---
title: ICorDebugRegisterSet::GetRegisters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
ms.openlocfilehash: 737993ac80b26d490915af3e97fd6a9552246aee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792118"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="01fb6-102">ICorDebugRegisterSet::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="01fb6-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="01fb6-103">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="01fb6-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01fb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01fb6-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="01fb6-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="01fb6-106">dans Masque de bits qui spécifie les valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="01fb6-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="01fb6-107">Chaque bit correspond à un registre.</span><span class="sxs-lookup"><span data-stu-id="01fb6-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="01fb6-108">Si un bit est défini sur un, la valeur du Registre est Récupérée ; dans le cas contraire, la valeur du Registre n’est pas récupérée.</span><span class="sxs-lookup"><span data-stu-id="01fb6-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="01fb6-109">dans Nombre de valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="01fb6-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="01fb6-110">à Tableau d’objets `CORDB_REGISTER`, chacun d’entre eux recevant une valeur de registre.</span><span class="sxs-lookup"><span data-stu-id="01fb6-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01fb6-111">Notes</span><span class="sxs-lookup"><span data-stu-id="01fb6-111">Remarks</span></span>  
 <span data-ttu-id="01fb6-112">La taille du tableau doit être égale au nombre de bits défini sur un dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="01fb6-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="01fb6-113">Le paramètre `regCount` spécifie le nombre d’éléments dans la mémoire tampon qui recevront les valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="01fb6-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="01fb6-114">Si la valeur `regCount` est trop petite pour le nombre de registres indiqué par le masque, les registres numérotés les plus élevés sont tronqués de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="01fb6-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="01fb6-115">Si la valeur `regCount` est trop grande, les éléments `regBuffer` inutilisés ne seront pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="01fb6-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="01fb6-116">Si le masque de bits spécifie un registre qui n’est pas disponible, `GetRegisters` retourne une valeur indéterminée pour ce registre.</span><span class="sxs-lookup"><span data-stu-id="01fb6-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01fb6-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="01fb6-117">Requirements</span></span>  
 <span data-ttu-id="01fb6-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01fb6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01fb6-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01fb6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01fb6-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01fb6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01fb6-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01fb6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fb6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01fb6-122">See also</span></span>

- [<span data-ttu-id="01fb6-123">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="01fb6-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="01fb6-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="01fb6-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
