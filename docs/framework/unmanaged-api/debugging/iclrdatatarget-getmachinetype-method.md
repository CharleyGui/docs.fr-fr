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
ms.openlocfilehash: 9d86b23b91702929a86334f557a8d647e19861a4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860589"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="9469e-102">ICLRDataTarget::GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="9469e-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="9469e-103">Obtient l’identificateur du type de jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="9469e-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9469e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9469e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9469e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9469e-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="9469e-106">à Pointeur vers une valeur qui indique le jeu d’instructions que le processus cible utilise.</span><span class="sxs-lookup"><span data-stu-id="9469e-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="9469e-107">Le retourné `machineType` est l’une des constantes de IMAGE_FILE_MACHINE, qui sont définies dans le fichier d’en-tête Winnt. h.</span><span class="sxs-lookup"><span data-stu-id="9469e-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9469e-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9469e-108">Requirements</span></span>  
 <span data-ttu-id="9469e-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9469e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9469e-110">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9469e-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9469e-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9469e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9469e-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9469e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9469e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9469e-113">See also</span></span>

- [<span data-ttu-id="9469e-114">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="9469e-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
