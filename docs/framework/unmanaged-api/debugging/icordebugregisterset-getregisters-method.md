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
ms.openlocfilehash: 40de06d47654337542d2c80dc325f8201335312a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379152"
---
# <a name="icordebugregistersetgetregisters-method"></a><span data-ttu-id="0a715-102">ICorDebugRegisterSet::GetRegisters, méthode</span><span class="sxs-lookup"><span data-stu-id="0a715-102">ICorDebugRegisterSet::GetRegisters Method</span></span>
<span data-ttu-id="0a715-103">Obtient la valeur de chaque registre (sur l’ordinateur qui exécute actuellement le code) spécifié par le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="0a715-103">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a715-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a715-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a715-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0a715-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="0a715-106">dans Masque de bits qui spécifie les valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0a715-106">[in] A bit mask that specifies which register values are to be retrieved.</span></span> <span data-ttu-id="0a715-107">Chaque bit correspond à un registre.</span><span class="sxs-lookup"><span data-stu-id="0a715-107">Each bit corresponds to a register.</span></span> <span data-ttu-id="0a715-108">Si un bit est défini sur un, la valeur du Registre est Récupérée ; dans le cas contraire, la valeur du Registre n’est pas récupérée.</span><span class="sxs-lookup"><span data-stu-id="0a715-108">If a bit is set to one, the register's value is retrieved; otherwise, the register's value is not retrieved.</span></span>  
  
 `regCount`  
 <span data-ttu-id="0a715-109">dans Nombre de valeurs de Registre à récupérer.</span><span class="sxs-lookup"><span data-stu-id="0a715-109">[in] The number of register values to be retrieved.</span></span>  
  
 `regBuffer`  
 <span data-ttu-id="0a715-110">à Tableau d' `CORDB_REGISTER` objets, chacun d’entre eux recevant une valeur d’un registre.</span><span class="sxs-lookup"><span data-stu-id="0a715-110">[out] An array of `CORDB_REGISTER` objects, each of which receives a value of a register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a715-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="0a715-111">Remarks</span></span>  
 <span data-ttu-id="0a715-112">La taille du tableau doit être égale au nombre de bits défini sur un dans le masque de bits.</span><span class="sxs-lookup"><span data-stu-id="0a715-112">The size of the array should be equal to the number of bits set to one in the bit mask.</span></span> <span data-ttu-id="0a715-113">Le `regCount` paramètre spécifie le nombre d’éléments dans la mémoire tampon qui recevront les valeurs de registre.</span><span class="sxs-lookup"><span data-stu-id="0a715-113">The `regCount` parameter specifies the number of elements in the buffer that will receive the register values.</span></span> <span data-ttu-id="0a715-114">Si la `regCount` valeur est trop petite pour le nombre de registres indiqué par le masque, les registres numérotés les plus élevés seront tronqués de l’ensemble.</span><span class="sxs-lookup"><span data-stu-id="0a715-114">If the `regCount` value is too small for the number of registers indicated by the mask, the higher numbered registers will be truncated from the set.</span></span> <span data-ttu-id="0a715-115">Si la `regCount` valeur est trop grande, les éléments inutilisés `regBuffer` ne seront pas modifiés.</span><span class="sxs-lookup"><span data-stu-id="0a715-115">If the `regCount` value is too large, the unused `regBuffer` elements will be unmodified.</span></span>  
  
 <span data-ttu-id="0a715-116">Si le masque de bits spécifie un registre qui n’est pas disponible, `GetRegisters` retourne une valeur indéterminée pour ce registre.</span><span class="sxs-lookup"><span data-stu-id="0a715-116">If the bit mask specifies a register that is unavailable, `GetRegisters` returns an indeterminate value for that register.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a715-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0a715-117">Requirements</span></span>  
 <span data-ttu-id="0a715-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a715-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a715-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a715-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a715-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a715-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a715-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a715-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a715-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a715-122">See also</span></span>

- [<span data-ttu-id="0a715-123">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="0a715-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="0a715-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="0a715-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
