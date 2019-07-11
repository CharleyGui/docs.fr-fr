---
title: CLRDataCreateInstance, fonction
ms.date: 03/30/2017
api_name:
- CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type:
- COM
f1_keywords:
- CLRDataCreateInstance
helpviewer_keywords:
- CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a839eb2edd36dc726c819a819fd4d427fbaea40
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740989"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="3e3b7-102">CLRDataCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="3e3b7-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="3e3b7-103">Crée un objet d’interface pour l’élément cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e3b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e3b7-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e3b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e3b7-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="3e3b7-106">[in] L’identificateur de l’interface à instancier.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="3e3b7-107">[in] Un pointeur vers un implémenté par l’utilisateur [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objet qui représente l’élément cible pour lequel créer l’objet d’interface.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="3e3b7-108">[out] Pointeur vers l’adresse de l’objet de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e3b7-109">Notes</span><span class="sxs-lookup"><span data-stu-id="3e3b7-109">Remarks</span></span>  
 <span data-ttu-id="3e3b7-110">Le `ICLRDataTarget` objet est implémenté par le writer de l’application de débogage.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="3e3b7-111">L’implémentation varie selon le type d’élément cible qui est représenté.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="3e3b7-112">L’élément cible peut être un processus, vidage de mémoire, ordinateur distant et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="3e3b7-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e3b7-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3e3b7-113">Requirements</span></span>  
 <span data-ttu-id="3e3b7-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e3b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e3b7-115">**En-tête :** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="3e3b7-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="3e3b7-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e3b7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e3b7-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e3b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e3b7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e3b7-118">See also</span></span>

- [<span data-ttu-id="3e3b7-119">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="3e3b7-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
