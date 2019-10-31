---
title: ICLRDataTarget::GetMachineType, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
ms.openlocfilehash: 941d1b4057ef78a6235a0ba853e48a000f2087e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122887"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="e42e5-102">ICLRDataTarget::GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="e42e5-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="e42e5-103">Obtient l’identificateur du type de jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="e42e5-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e42e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e42e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e42e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e42e5-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="e42e5-106">à Pointeur vers une valeur qui indique le jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="e42e5-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="e42e5-107">La `machineType` retournée est l’une des constantes IMAGE_FILE_MACHINE, qui sont définies dans le fichier d’en-tête Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="e42e5-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e42e5-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="e42e5-108">Requirements</span></span>  
 <span data-ttu-id="e42e5-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e42e5-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e42e5-110">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="e42e5-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e42e5-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e42e5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e42e5-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e42e5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e42e5-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e42e5-113">See also</span></span>

- [<span data-ttu-id="e42e5-114">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="e42e5-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
