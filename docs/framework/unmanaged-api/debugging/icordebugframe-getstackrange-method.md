---
title: ICorDebugFrame::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178911"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="1f512-102">ICorDebugFrame::GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="1f512-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="1f512-103">Obtient la plage d’adresse absolue de ce cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="1f512-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f512-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f512-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f512-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1f512-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="1f512-106">[out] Un pointeur `CORDB_ADDRESS` à un qui spécifie l’adresse de départ du cadre de pile représenté par cet `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="1f512-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="1f512-107">[out] Un pointeur `CORDB_ADDRESS` à un qui spécifie l’adresse de fin du cadre de pile représenté par cet `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="1f512-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f512-108">Notes </span><span class="sxs-lookup"><span data-stu-id="1f512-108">Remarks</span></span>  
 <span data-ttu-id="1f512-109">La portée d’adresse de la pile est utile pour reconstituer les traces de piles entrelacées recueillies à partir de moteurs de débogage multiples.</span><span class="sxs-lookup"><span data-stu-id="1f512-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="1f512-110">La plage numérique ne fournit aucune information sur le contenu du cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="1f512-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="1f512-111">Il est significatif seulement pour la comparaison des emplacements de cadre de pile.</span><span class="sxs-lookup"><span data-stu-id="1f512-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f512-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1f512-112">Requirements</span></span>  
 <span data-ttu-id="1f512-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f512-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f512-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f512-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f512-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f512-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f512-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f512-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
