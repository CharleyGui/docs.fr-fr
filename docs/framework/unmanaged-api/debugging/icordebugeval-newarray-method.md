---
title: ICorDebugEval::NewArray, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
ms.openlocfilehash: ca0844e4d2b1cad65266d58c6cda74de203d1758
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137660"
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="81333-102">ICorDebugEval::NewArray, méthode</span><span class="sxs-lookup"><span data-stu-id="81333-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="81333-103">Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.</span><span class="sxs-lookup"><span data-stu-id="81333-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="81333-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="81333-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="81333-105">Utilisez [ICorDebugEval2 :: NewParameterizedArray,](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="81333-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81333-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81333-106">Syntax</span></span>  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81333-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81333-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="81333-108">dans Valeur de l’énumération CorElementType qui spécifie le type d’élément du tableau.</span><span class="sxs-lookup"><span data-stu-id="81333-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="81333-109">dans Pointeur vers un objet ICorDebugClass qui spécifie la classe de l’élément.</span><span class="sxs-lookup"><span data-stu-id="81333-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="81333-110">Cette valeur peut être null si le type d’élément est un type primitif.</span><span class="sxs-lookup"><span data-stu-id="81333-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="81333-111">dans Nombre de dimensions du tableau.</span><span class="sxs-lookup"><span data-stu-id="81333-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="81333-112">Dans le .NET Framework 2,0, cette valeur doit être 1.</span><span class="sxs-lookup"><span data-stu-id="81333-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="81333-113">dans Taille, en octets, de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="81333-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="81333-114">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="81333-114">[in] Optional.</span></span> <span data-ttu-id="81333-115">Limite inférieure de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="81333-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="81333-116">Si cette valeur est omise, une limite inférieure de zéro est utilisée pour chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="81333-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81333-117">Notes</span><span class="sxs-lookup"><span data-stu-id="81333-117">Remarks</span></span>  
 <span data-ttu-id="81333-118">Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="81333-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81333-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="81333-119">Requirements</span></span>  
 <span data-ttu-id="81333-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81333-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81333-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81333-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81333-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81333-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81333-123">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="81333-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
