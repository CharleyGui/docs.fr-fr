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
ms.openlocfilehash: 2149c985519b95f89af2c50d05753ae7259babe4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378220"
---
# <a name="icordebugregisterset2getregistersavailable-method"></a><span data-ttu-id="85887-102">ICorDebugRegisterSet2::GetRegistersAvailable, méthode</span><span class="sxs-lookup"><span data-stu-id="85887-102">ICorDebugRegisterSet2::GetRegistersAvailable Method</span></span>
<span data-ttu-id="85887-103">Obtient un tableau d’octets qui fournit une bitmap des registres disponibles.</span><span class="sxs-lookup"><span data-stu-id="85887-103">Gets an array of bytes that provides a bitmap of the available registers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85887-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85887-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [in] ULONG32 numChunks,  
    [out, size_is(numChunks)] BYTE availableRegChunks[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85887-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85887-105">Parameters</span></span>  
 `numChunks`  
 <span data-ttu-id="85887-106">[in] Taille du tableau `availableRegChunks`.</span><span class="sxs-lookup"><span data-stu-id="85887-106">[in] The size of the `availableRegChunks` array.</span></span>  
  
 `availableRegChunks`  
 <span data-ttu-id="85887-107">à Tableau d’octets, chacun d’eux correspondant à un registre.</span><span class="sxs-lookup"><span data-stu-id="85887-107">[out] An array of bytes, each bit of which corresponds to a register.</span></span> <span data-ttu-id="85887-108">Si un registre est disponible, le bit correspondant du Registre est défini.</span><span class="sxs-lookup"><span data-stu-id="85887-108">If a register is available, the register's corresponding bit is set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85887-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="85887-109">Remarks</span></span>  
 <span data-ttu-id="85887-110">Les valeurs de l’énumération CorDebugRegister spécifient les registres de différents microprocesseurs.</span><span class="sxs-lookup"><span data-stu-id="85887-110">The values of the CorDebugRegister enumeration specify the registers of different microprocessors.</span></span> <span data-ttu-id="85887-111">Les cinq bits supérieurs de chaque valeur correspondent à l’index dans le `availableRegChunks` tableau d’octets.</span><span class="sxs-lookup"><span data-stu-id="85887-111">The upper five bits of each value are the index into the `availableRegChunks` array of bytes.</span></span> <span data-ttu-id="85887-112">Les trois bits de poids faible de chaque valeur identifient la position du bit dans l’octet indexé.</span><span class="sxs-lookup"><span data-stu-id="85887-112">The lower three bits of each value identify the bit position within the indexed byte.</span></span> <span data-ttu-id="85887-113">À partir d’une `CorDebugRegister` valeur qui spécifie un registre particulier, la position du Registre dans le masque est déterminée comme suit :</span><span class="sxs-lookup"><span data-stu-id="85887-113">Given a `CorDebugRegister` value that specifies a particular register, the register's position in the mask is determined as follows:</span></span>  
  
1. <span data-ttu-id="85887-114">Extrayez l’index nécessaire pour accéder à l’octet correct dans le `availableRegChunks` tableau :</span><span class="sxs-lookup"><span data-stu-id="85887-114">Extract the index needed to access the correct byte in the `availableRegChunks` array:</span></span>  
  
     <span data-ttu-id="85887-115">`CorDebugRegister`valeur >> 3</span><span class="sxs-lookup"><span data-stu-id="85887-115">`CorDebugRegister` value >> 3</span></span>  
  
2. <span data-ttu-id="85887-116">Extrayez la position du bit dans l’octet indexé, où le bit zéro est le bit le moins significatif :</span><span class="sxs-lookup"><span data-stu-id="85887-116">Extract the bit position within the indexed byte, where bit zero is the least significant bit:</span></span>  
  
     <span data-ttu-id="85887-117">`CorDebugRegister`valeur & 7</span><span class="sxs-lookup"><span data-stu-id="85887-117">`CorDebugRegister` value & 7</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85887-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85887-118">Requirements</span></span>  
 <span data-ttu-id="85887-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85887-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85887-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85887-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85887-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85887-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85887-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85887-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85887-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85887-123">See also</span></span>

- [<span data-ttu-id="85887-124">ICorDebugRegisterSet2, interface</span><span class="sxs-lookup"><span data-stu-id="85887-124">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
- [<span data-ttu-id="85887-125">ICorDebugRegisterSet, interface</span><span class="sxs-lookup"><span data-stu-id="85887-125">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
