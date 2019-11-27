---
title: ISymUnmanagedVariable::GetEndOffset, méthode
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 4ac1fc0b3567c49dfb36d2886926bee72d62a8dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446064"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="b3adc-102">ISymUnmanagedVariable::GetEndOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="b3adc-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="b3adc-103">Obtient le décalage de fin de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="b3adc-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="b3adc-104">S’il s’agit d’une variable locale dans une étendue, le décalage de fin se situe dans les offsets définis pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="b3adc-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3adc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3adc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3adc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b3adc-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b3adc-107">à Pointeur vers un `ULONG32` qui reçoit le décalage de fin.</span><span class="sxs-lookup"><span data-stu-id="b3adc-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3adc-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b3adc-108">Return Value</span></span>  
 <span data-ttu-id="b3adc-109">S_OK si la méthode est réussie ; Sinon, E_FAIL ou un autre code d’erreur.</span><span class="sxs-lookup"><span data-stu-id="b3adc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3adc-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b3adc-110">Requirements</span></span>  
 <span data-ttu-id="b3adc-111">**En-tête :** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b3adc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3adc-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3adc-112">See also</span></span>

- [<span data-ttu-id="b3adc-113">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="b3adc-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="b3adc-114">GetStartOffset, méthode</span><span class="sxs-lookup"><span data-stu-id="b3adc-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
