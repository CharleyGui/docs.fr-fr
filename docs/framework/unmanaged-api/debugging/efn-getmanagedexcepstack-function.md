---
title: _EFN_GetManagedExcepStack, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f4e057a487462feb385ca0e3ca977fdd165f56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739094"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="479e5-102">\_EFN\_GetManagedExcepStack (fonction)</span><span class="sxs-lookup"><span data-stu-id="479e5-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="479e5-103">Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.</span><span class="sxs-lookup"><span data-stu-id="479e5-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="479e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="479e5-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="479e5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="479e5-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="479e5-106">[in] Le client en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="479e5-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="479e5-107">[in] Un pointeur d’objet managé, dérivé <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="479e5-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="479e5-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="479e5-108">szStackString</span></span>  
 <span data-ttu-id="479e5-109">[out] La chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="479e5-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="479e5-110">[out] Le nombre de caractères disponibles dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="479e5-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="479e5-111">Notes</span><span class="sxs-lookup"><span data-stu-id="479e5-111">Remarks</span></span>  
 <span data-ttu-id="479e5-112">S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne les HRESULT SOS_E_NOMANAGEDCODE avec une valeur de 0xa0 et un code d’erreur de 0 x 1000.</span><span class="sxs-lookup"><span data-stu-id="479e5-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="479e5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="479e5-113">Requirements</span></span>  
 <span data-ttu-id="479e5-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="479e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="479e5-115">**En-tête :** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="479e5-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="479e5-116">**Version du .NET framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="479e5-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479e5-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="479e5-117">See also</span></span>

- [<span data-ttu-id="479e5-118">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="479e5-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
