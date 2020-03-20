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
ms.openlocfilehash: 32e899622b9c649a08e3bca1b6645f70dcbcbb19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178541"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="b691a-102">ICorDebugRegisterSet::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="b691a-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="b691a-103">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) qui est spécifié par le masque bit.</span><span class="sxs-lookup"><span data-stu-id="b691a-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b691a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b691a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b691a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b691a-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="b691a-106">[dans] Un masque qui précise quelles valeurs d’enregistrement doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="b691a-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="b691a-107">Chaque bit correspond à un registre.</span><span class="sxs-lookup"><span data-stu-id="b691a-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="b691a-108">Si un peu est réglé à un, la valeur du registre est récupérée; autrement, la valeur du registre n’est pas récupérée.</span><span class="sxs-lookup"><span data-stu-id="b691a-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="b691a-109">[dans] Nombre de valeurs de registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="b691a-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="b691a-110">[out] Une gamme `CORDB_REGISTER` d’objets, dont chacun reçoit une valeur d’un registre.</span><span class="sxs-lookup"><span data-stu-id="b691a-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b691a-111">Notes </span><span class="sxs-lookup"><span data-stu-id="b691a-111">Remarks</span></span>  
 <span data-ttu-id="b691a-112">La taille du tableau doit être égale au nombre de bits réglés à un dans le masque de bit.</span><span class="sxs-lookup"><span data-stu-id="b691a-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="b691a-113">Le `regCount` paramètre précise le nombre d’éléments dans le tampon qui recevront les valeurs du registre.</span><span class="sxs-lookup"><span data-stu-id="b691a-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="b691a-114">Si `regCount` la valeur est trop faible pour le nombre de registres indiqués par le masque, les registres numérotés plus élevés seront tronqués à partir de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="b691a-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="b691a-115">Si `regCount` la valeur est trop `regBuffer` grande, les éléments inutilisés ne seront pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="b691a-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="b691a-116">Si le masque bit spécifie `GetRegisters` un registre qui n’est pas disponible, renvoie une valeur indéterminée pour ce registre.</span><span class="sxs-lookup"><span data-stu-id="b691a-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b691a-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b691a-117">Requirements</span></span>  
 <span data-ttu-id="b691a-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b691a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b691a-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b691a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b691a-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b691a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b691a-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b691a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b691a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b691a-122">See also</span></span>

- [<span data-ttu-id="b691a-123">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="b691a-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="b691a-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="b691a-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
