---
title: ICorDebugILFrame::EnumerateArguments, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateArguments
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateArguments
helpviewer_keywords:
- ICorDebugILFrame::EnumerateArguments method [.NET Framework debugging]
- EnumerateArguments method [.NET Framework debugging]
ms.assetid: 00ac81e2-a774-422a-bd88-54a4b3c99f73
topic_type:
- apiref
ms.openlocfilehash: 9b0bc59b67b5d4b2184733f22616433bf33be616
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703224"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="413bc-102">ICorDebugILFrame::EnumerateArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="413bc-102">ICorDebugILFrame::EnumerateArguments Method</span></span>

<span data-ttu-id="413bc-103">Obtient un énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="413bc-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="413bc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="413bc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="413bc-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="413bc-106">à Pointeur vers l’adresse d’un objet ICorDebugValueEnum qui est l’énumérateur des arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="413bc-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="413bc-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="413bc-107">Remarks</span></span>  

 <span data-ttu-id="413bc-108">`EnumerateArguments` Obtient un énumérateur qui peut répertorier les arguments disponibles dans le frame d’appel représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="413bc-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="413bc-109">La liste inclut les arguments [vararg](/cpp/windows/vararg) (autrement dit, un nombre variable d’arguments) ainsi que les arguments qui ne le sont pas `vararg` .</span><span class="sxs-lookup"><span data-stu-id="413bc-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413bc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="413bc-110">Requirements</span></span>  

 <span data-ttu-id="413bc-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="413bc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413bc-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="413bc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="413bc-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="413bc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="413bc-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="413bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
