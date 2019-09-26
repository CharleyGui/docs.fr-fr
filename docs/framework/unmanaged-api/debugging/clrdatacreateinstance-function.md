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
ms.openlocfilehash: a5d44f9b5dc42147959d3f1d127a64d39258f515
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274261"
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="4165c-102">CLRDataCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="4165c-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="4165c-103">Crée un objet d’interface pour l’élément cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="4165c-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4165c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4165c-104">Syntax</span></span>  
  
```cpp  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4165c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4165c-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="4165c-106">dans Identificateur de l’interface à instancier.</span><span class="sxs-lookup"><span data-stu-id="4165c-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="4165c-107">dans Pointeur vers un objet [ICLRDataTarget](iclrdatatarget-interface.md) implémenté par l’utilisateur qui représente l’élément cible pour lequel créer l’objet d’interface.</span><span class="sxs-lookup"><span data-stu-id="4165c-107">[in] A pointer to a user-implemented [ICLRDataTarget](iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="4165c-108">à Pointeur vers l’adresse de l’objet d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="4165c-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4165c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="4165c-109">Remarks</span></span>  
 <span data-ttu-id="4165c-110">L' `ICLRDataTarget` objet est implémenté par le writer de l’application de débogage.</span><span class="sxs-lookup"><span data-stu-id="4165c-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="4165c-111">L’implémentation dépend du type d’élément cible représenté.</span><span class="sxs-lookup"><span data-stu-id="4165c-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="4165c-112">L’élément cible peut être un processus, un vidage de la mémoire, un ordinateur distant, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="4165c-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4165c-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4165c-113">Requirements</span></span>  
 <span data-ttu-id="4165c-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4165c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4165c-115">**En-tête :** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="4165c-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="4165c-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4165c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4165c-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4165c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4165c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4165c-118">See also</span></span>

- [<span data-ttu-id="4165c-119">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="4165c-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
