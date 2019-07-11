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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 958968fb1a84b598b0c3e92151fbad58fc5e79d4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738739"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="99ea6-102">ICLRDataTarget::GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="99ea6-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="99ea6-103">Obtient l’identificateur pour le genre de jeu d’instructions qui utilise le processus cible.</span><span class="sxs-lookup"><span data-stu-id="99ea6-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99ea6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99ea6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99ea6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99ea6-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="99ea6-106">[out] Utilisation d’un pointeur vers une valeur qui indique le jeu d’instructions que le processus cible.</span><span class="sxs-lookup"><span data-stu-id="99ea6-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="99ea6-107">Retourné `machineType` est une des constantes IMAGE_FILE_MACHINE qui sont définies dans le fichier d’en-tête WinNT.h.</span><span class="sxs-lookup"><span data-stu-id="99ea6-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99ea6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="99ea6-108">Requirements</span></span>  
 <span data-ttu-id="99ea6-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99ea6-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99ea6-110">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="99ea6-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="99ea6-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99ea6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99ea6-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99ea6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ea6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99ea6-113">See also</span></span>

- [<span data-ttu-id="99ea6-114">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="99ea6-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
