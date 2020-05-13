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
ms.openlocfilehash: ad1a91e42f582ce96906da5cbf00ca89acb18499
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210291"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="650bf-102">ICorDebugILFrame::EnumerateLocalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="650bf-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>
<span data-ttu-id="650bf-103">Obtient un énumérateur pour les variables locales dans ce frame.</span><span class="sxs-lookup"><span data-stu-id="650bf-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="650bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="650bf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="650bf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="650bf-105">Parameters</span></span>  
 `ppValueEnum`  
 <span data-ttu-id="650bf-106">[en sortie] Un pointeur vers l'adresse d'un objet ICorDebugValueEnum qui est l'énumérateur pour les variables locales de ce frame.</span><span class="sxs-lookup"><span data-stu-id="650bf-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="650bf-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="650bf-107">Remarks</span></span>  
 <span data-ttu-id="650bf-108">`EnumerateLocalVariables`Obtient un énumérateur qui peut répertorier les variables locales disponibles dans le frame d’appel qui est représenté par cet objet ICorDebugILFrame.</span><span class="sxs-lookup"><span data-stu-id="650bf-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="650bf-109">La liste peut ne pas inclure toutes les variables locales dans la fonction en cours d’exécution, car certaines d’entre elles peuvent ne pas être actives.</span><span class="sxs-lookup"><span data-stu-id="650bf-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="650bf-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="650bf-110">Requirements</span></span>  
 <span data-ttu-id="650bf-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="650bf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="650bf-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="650bf-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="650bf-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="650bf-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="650bf-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="650bf-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
