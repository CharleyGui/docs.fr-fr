---
title: PFN_CLRDataCreateInstance (pointeur fonction)
ms.date: 03/30/2017
api_name:
- PFN_CLRDataCreateInstance
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- PFN_CLRDataCreateInstance
helpviewer_keywords:
- PFN_CLRDataCreateInstance function pointer [.NET Framework debugging]
ms.assetid: 5c66ac57-d751-4de5-af9f-26ceb949af8b
topic_type:
- apiref
ms.openlocfilehash: 433f34447d3bd1a57ca1e289cb0eab3facac2c69
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790354"
---
# <a name="pfn_clrdatacreateinstance-function-pointer"></a><span data-ttu-id="497b7-102">PFN_CLRDataCreateInstance (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="497b7-102">PFN_CLRDataCreateInstance Function Pointer</span></span>
<span data-ttu-id="497b7-103">Pointe vers une fonction qui crée un objet d’interface pour l’élément cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="497b7-103">Points to a function that creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="497b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="497b7-104">Syntax</span></span>  
  
```cpp  
typedef HRESULT (STDAPICALLTYPE* PFN_CLRDataCreateInstance) (  
    [in]  REFIID           iid,  
    [in]  ICLRDataTarget  *target,  
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="497b7-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="497b7-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="497b7-106">dans Identificateur de l’interface à instancier.</span><span class="sxs-lookup"><span data-stu-id="497b7-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="497b7-107">dans Pointeur vers un objet [ICLRDataTarget](iclrdatatarget-interface.md) implémenté par l’utilisateur qui représente l’élément cible pour lequel créer l’objet d’interface.</span><span class="sxs-lookup"><span data-stu-id="497b7-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="497b7-108">à Pointeur vers l’adresse de l’objet d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="497b7-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="497b7-109">Notes</span><span class="sxs-lookup"><span data-stu-id="497b7-109">Remarks</span></span>  
 <span data-ttu-id="497b7-110">L’objet `ICLRDataTarget` est implémenté par le writer de l’application de débogage.</span><span class="sxs-lookup"><span data-stu-id="497b7-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="497b7-111">L’implémentation dépend du type d’élément cible représenté.</span><span class="sxs-lookup"><span data-stu-id="497b7-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="497b7-112">L’élément cible peut être un processus, un vidage de la mémoire, un ordinateur distant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="497b7-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="497b7-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="497b7-113">Requirements</span></span>  
 <span data-ttu-id="497b7-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="497b7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="497b7-115">**En-tête :** ClrData. idl</span><span class="sxs-lookup"><span data-stu-id="497b7-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="497b7-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="497b7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="497b7-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="497b7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="497b7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="497b7-118">See also</span></span>

- [<span data-ttu-id="497b7-119">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="497b7-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
