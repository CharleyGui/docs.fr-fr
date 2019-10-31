---
title: ICorDebugILFrame::EnumerateLocalVariables, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 07331a512dd513a94a7d8c3a8d8b0754d998b94b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131003"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="32548-102">ICorDebugILFrame::EnumerateLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="32548-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="32548-103">Obtient un énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="32548-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32548-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32548-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(   
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32548-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32548-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="32548-106">à Pointeur vers l’adresse d’un objet ICorDebugValueEnum qui est l’énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="32548-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32548-107">Notes</span><span class="sxs-lookup"><span data-stu-id="32548-107">Remarks</span></span>  
 <span data-ttu-id="32548-108">`EnumerateLocalVariables` obtient un énumérateur qui peut répertorier les variables locales disponibles dans le frame d’appel qui est représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="32548-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="32548-109">La liste peut ne pas inclure toutes les variables locales dans la fonction en cours d’exécution, car certaines d’entre elles peuvent ne pas être actives.</span><span class="sxs-lookup"><span data-stu-id="32548-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32548-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="32548-110">Requirements</span></span>  
 <span data-ttu-id="32548-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32548-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32548-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32548-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32548-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32548-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32548-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32548-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
