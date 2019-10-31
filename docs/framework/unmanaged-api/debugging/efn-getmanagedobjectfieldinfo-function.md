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
ms.openlocfilehash: b68f24908a5b214d507da8e8a4636a7c55259604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123020"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="ce8dd-102">\_EFN\_fonction GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="ce8dd-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="ce8dd-103">Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce8dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce8dd-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce8dd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce8dd-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ce8dd-106">dans Pointeur vers le client de débogage.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="ce8dd-107">dans Pointeur d’objet managé.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="ce8dd-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="ce8dd-108">szFieldName</span></span>  
 <span data-ttu-id="ce8dd-109">dans Pointeur d’objet managé vers le nom de champ.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ce8dd-110">à Valeur de champ.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-110">[out] The field value.</span></span> <span data-ttu-id="ce8dd-111">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="ce8dd-112">à Offset de `objAddr` au champ.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="ce8dd-113">Ce paramètre peut avoir la valeur Null.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce8dd-114">Notes</span><span class="sxs-lookup"><span data-stu-id="ce8dd-114">Remarks</span></span>  
 <span data-ttu-id="ce8dd-115">Si le décalage est égal à 0, aucun décalage n’est écrit.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="ce8dd-116">S’il n’existe pas de code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec la valeur d’installation 0xa0 et le code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="ce8dd-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce8dd-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="ce8dd-117">Requirements</span></span>  
 <span data-ttu-id="ce8dd-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce8dd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce8dd-119">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="ce8dd-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="ce8dd-120">**Version de .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce8dd-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8dd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce8dd-121">See also</span></span>

- [<span data-ttu-id="ce8dd-122">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="ce8dd-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
