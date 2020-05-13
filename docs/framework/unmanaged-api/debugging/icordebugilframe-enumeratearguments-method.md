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
ms.openlocfilehash: 3945b1dea62dc0616d669356faf60f0d09cfb084
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210304"
---
# <a name="icordebugilframeenumeratearguments-method"></a><span data-ttu-id="48770-102">ICorDebugILFrame::EnumerateArguments, méthode</span><span class="sxs-lookup"><span data-stu-id="48770-102">ICorDebugILFrame::EnumerateArguments Method</span></span>
<span data-ttu-id="48770-103">Obtient un énumérateur pour les arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="48770-103">Gets an enumerator for the arguments in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48770-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48770-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateArguments (  
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48770-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48770-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="48770-106">à Pointeur vers l’adresse d’un objet ICorDebugValueEnum qui est l’énumérateur des arguments dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="48770-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the arguments in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48770-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="48770-107">Remarks</span></span>  
 <span data-ttu-id="48770-108">`EnumerateArguments`Obtient un énumérateur qui peut répertorier les arguments disponibles dans le frame d’appel représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="48770-108">`EnumerateArguments` gets an enumerator that can list the arguments available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="48770-109">La liste inclut les arguments [vararg](/cpp/windows/vararg) (autrement dit, un nombre variable d’arguments) ainsi que les arguments qui ne le sont pas `vararg` .</span><span class="sxs-lookup"><span data-stu-id="48770-109">The list will include arguments that are [vararg](/cpp/windows/vararg) (that is, a variable number of arguments) as well as arguments that are not `vararg`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48770-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="48770-110">Requirements</span></span>  
 <span data-ttu-id="48770-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48770-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48770-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48770-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48770-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48770-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48770-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48770-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
