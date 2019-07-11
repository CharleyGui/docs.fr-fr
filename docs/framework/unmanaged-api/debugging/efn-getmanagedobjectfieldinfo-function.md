---
title: _EFN_GetManagedObjectFieldInfo, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739002"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="61743-102">\_EFN\_GetManagedObjectFieldInfo Function</span><span class="sxs-lookup"><span data-stu-id="61743-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="61743-103">Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.</span><span class="sxs-lookup"><span data-stu-id="61743-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61743-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61743-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61743-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61743-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="61743-106">[in] Pointeur vers le client de débogage.</span><span class="sxs-lookup"><span data-stu-id="61743-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="61743-107">[in] Un pointeur d’objet managé.</span><span class="sxs-lookup"><span data-stu-id="61743-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="61743-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="61743-108">szFieldName</span></span>  
 <span data-ttu-id="61743-109">[in] Un pointeur d’objet managé pour le nom du champ.</span><span class="sxs-lookup"><span data-stu-id="61743-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="61743-110">[out] La valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="61743-110">[out] The field value.</span></span> <span data-ttu-id="61743-111">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="61743-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="61743-112">[out] Le décalage à partir de `objAddr` au champ.</span><span class="sxs-lookup"><span data-stu-id="61743-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="61743-113">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="61743-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61743-114">Notes</span><span class="sxs-lookup"><span data-stu-id="61743-114">Remarks</span></span>  
 <span data-ttu-id="61743-115">Si le décalage est 0, aucun offset n’est écrit.</span><span class="sxs-lookup"><span data-stu-id="61743-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="61743-116">S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne les HRESULT SOS_E_NOMANAGEDCODE avec une valeur de 0xa0 et un code d’erreur de 0 x 1000.</span><span class="sxs-lookup"><span data-stu-id="61743-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61743-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61743-117">Requirements</span></span>  
 <span data-ttu-id="61743-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61743-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61743-119">**En-tête :** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="61743-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="61743-120">**Version du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61743-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61743-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61743-121">See also</span></span>

- [<span data-ttu-id="61743-122">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="61743-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
