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
ms.openlocfilehash: 9bcc03cc97a62b4c1cadacd7c0b2bc46b9fec470
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134140"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="8868f-102">\_EFN\_fonction GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="8868f-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="8868f-103">Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.</span><span class="sxs-lookup"><span data-stu-id="8868f-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8868f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8868f-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8868f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8868f-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8868f-106">dans Client en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="8868f-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="8868f-107">dans Pointeur d’objet managé, dérivé de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="8868f-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="8868f-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="8868f-108">szStackString</span></span>  
 <span data-ttu-id="8868f-109">à Chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="8868f-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="8868f-110">à Nombre de caractères disponibles dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="8868f-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8868f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="8868f-111">Remarks</span></span>  
 <span data-ttu-id="8868f-112">S’il n’existe pas de code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec la valeur d’installation 0xa0 et le code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="8868f-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8868f-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="8868f-113">Requirements</span></span>  
 <span data-ttu-id="8868f-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8868f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8868f-115">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="8868f-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8868f-116">**Version de .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8868f-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8868f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8868f-117">See also</span></span>

- [<span data-ttu-id="8868f-118">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="8868f-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
