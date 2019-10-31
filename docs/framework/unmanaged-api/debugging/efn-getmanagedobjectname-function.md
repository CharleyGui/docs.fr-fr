---
title: _EFN_GetManagedObjectName, fonction
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123009"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="c84f7-102">\_EFN\_fonction GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="c84f7-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="c84f7-103">Obtient le nom d’un type à l’aide du pointeur d’objet managé fourni.</span><span class="sxs-lookup"><span data-stu-id="c84f7-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c84f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c84f7-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c84f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c84f7-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="c84f7-106">dans Pointeur vers le client de débogage.</span><span class="sxs-lookup"><span data-stu-id="c84f7-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="c84f7-107">dans Pointeur d’objet managé.</span><span class="sxs-lookup"><span data-stu-id="c84f7-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="c84f7-108">szName</span><span class="sxs-lookup"><span data-stu-id="c84f7-108">szName</span></span>  
 <span data-ttu-id="c84f7-109">à Nom du type.</span><span class="sxs-lookup"><span data-stu-id="c84f7-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="c84f7-110">à Nombre de caractères disponibles dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c84f7-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c84f7-111">Notes</span><span class="sxs-lookup"><span data-stu-id="c84f7-111">Remarks</span></span>  
 <span data-ttu-id="c84f7-112">S’il n’existe pas de code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec la valeur d’installation 0xa0 et le code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="c84f7-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c84f7-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="c84f7-113">Requirements</span></span>  
 <span data-ttu-id="c84f7-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c84f7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c84f7-115">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="c84f7-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="c84f7-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c84f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c84f7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c84f7-117">See also</span></span>

- [<span data-ttu-id="c84f7-118">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="c84f7-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
