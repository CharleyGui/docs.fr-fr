---
title: ICorDebugRegisterSet2::GetRegistersAvailable, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::GetRegistersAvailable
helpviewer_keywords:
- GetRegistersAvailable method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
- ICorDebugRegisterSet2::GetRegistersAvailable method [.NET Framework debugging]
ms.assetid: f3ed344b-0d3a-44e8-8000-2a97e0805a2c
topic_type:
- apiref
ms.openlocfilehash: d0b6960a24e246c7a538e8ffc59fa380a4b8e2a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131370"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="d1290-102">ICorDebugRegisterSet2::GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="d1290-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="d1290-103">Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.</span><span class="sxs-lookup"><span data-stu-id="d1290-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1290-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1290-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1290-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d1290-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="d1290-106">[in] Taille du tableau `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="d1290-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="d1290-107">à Tableau d’octets, chacun d’eux correspondant à un registre.</span><span class="sxs-lookup"><span data-stu-id="d1290-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="d1290-108">Si un registre est disponible, le bit correspondant du Registre est défini.</span><span class="sxs-lookup"><span data-stu-id="d1290-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1290-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d1290-109">Remarks</span></span>  
 <span data-ttu-id="d1290-110">Les valeurs de l’énumération CorDebugRegister spécifient les registres de différents microprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="d1290-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="d1290-111">Les cinq bits supérieurs de chaque valeur sont l’index dans le tableau `availableRegChunks` d’octets.</span><span class="sxs-lookup"><span data-stu-id="d1290-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="d1290-112">Les trois bits de poids faible de chaque valeur identifient la position du bit dans l’octet indexé.</span><span class="sxs-lookup"><span data-stu-id="d1290-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="d1290-113">Étant donné une valeur `CorDebugRegister` qui spécifie un registre particulier, la position du Registre dans le masque est déterminée comme suit :</span><span class="sxs-lookup"><span data-stu-id="d1290-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="d1290-114">Extrayez l’index nécessaire pour accéder à l’octet correct dans le tableau `availableRegChunks` :</span><span class="sxs-lookup"><span data-stu-id="d1290-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="d1290-115">valeur `CorDebugRegister` > > 3</span><span class="sxs-lookup"><span data-stu-id="d1290-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="d1290-116">Extrayez la position du bit dans l’octet indexé, où le bit zéro est le bit le moins significatif :</span><span class="sxs-lookup"><span data-stu-id="d1290-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="d1290-117">valeur `CorDebugRegister` & 7</span><span class="sxs-lookup"><span data-stu-id="d1290-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1290-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="d1290-118">Requirements</span></span>  
 <span data-ttu-id="d1290-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1290-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1290-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1290-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1290-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1290-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1290-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1290-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1290-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1290-123">See also</span></span>

- [<span data-ttu-id="d1290-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="d1290-124">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
- [<span data-ttu-id="d1290-125">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="d1290-125">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
