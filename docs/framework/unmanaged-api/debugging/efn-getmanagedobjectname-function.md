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
ms.openlocfilehash: 0fb694cf85256c0f3ac5ae179e53ff504ab707e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676203"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="6af65-102">\_EFN \_ fonction GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="6af65-102">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="6af65-103">Obtient le nom d’un type à l’aide du pointeur d’objet managé fourni.</span><span class="sxs-lookup"><span data-stu-id="6af65-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af65-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6af65-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af65-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6af65-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="6af65-106">dans Pointeur vers le client de débogage.</span><span class="sxs-lookup"><span data-stu-id="6af65-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="6af65-107">dans Pointeur d’objet managé.</span><span class="sxs-lookup"><span data-stu-id="6af65-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="6af65-108">szName</span><span class="sxs-lookup"><span data-stu-id="6af65-108">szName</span></span>  
 <span data-ttu-id="6af65-109">à Nom du type.</span><span class="sxs-lookup"><span data-stu-id="6af65-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="6af65-110">à Nombre de caractères disponibles dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="6af65-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6af65-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="6af65-111">Remarks</span></span>  

 <span data-ttu-id="6af65-112">S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec une valeur d’installation de 0xa0 et un code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="6af65-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af65-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6af65-113">Requirements</span></span>  

 <span data-ttu-id="6af65-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af65-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af65-115">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="6af65-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="6af65-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af65-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af65-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6af65-117">See also</span></span>

- [<span data-ttu-id="6af65-118">Fonctions statiques globales du débogage</span><span class="sxs-lookup"><span data-stu-id="6af65-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
