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
ms.openlocfilehash: c50fe09648793ba7340960654811ff31187269d8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860789"
---
# <a name="_efn_getmanagedexcepstack-function"></a><span data-ttu-id="31ff4-102">\_EFN\_fonction GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="31ff4-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="31ff4-103">Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.</span><span class="sxs-lookup"><span data-stu-id="31ff4-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31ff4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31ff4-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31ff4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="31ff4-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="31ff4-106">dans Client en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="31ff4-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="31ff4-107">dans Pointeur d’objet managé, dérivé de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="31ff4-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="31ff4-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="31ff4-108">szStackString</span></span>  
 <span data-ttu-id="31ff4-109">à Chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="31ff4-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="31ff4-110">à Nombre de caractères disponibles dans la mémoire tampon de chaîne.</span><span class="sxs-lookup"><span data-stu-id="31ff4-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31ff4-111">Notes </span><span class="sxs-lookup"><span data-stu-id="31ff4-111">Remarks</span></span>  
 <span data-ttu-id="31ff4-112">S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne HRESULT SOS_E_NOMANAGEDCODE avec une valeur d’installation de 0xa0 et un code d’erreur 0x1000.</span><span class="sxs-lookup"><span data-stu-id="31ff4-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31ff4-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="31ff4-113">Requirements</span></span>  
 <span data-ttu-id="31ff4-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31ff4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31ff4-115">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="31ff4-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="31ff4-116">**Version de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31ff4-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31ff4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31ff4-117">See also</span></span>

- [<span data-ttu-id="31ff4-118">Fonctions statiques globales du débogage</span><span class="sxs-lookup"><span data-stu-id="31ff4-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
