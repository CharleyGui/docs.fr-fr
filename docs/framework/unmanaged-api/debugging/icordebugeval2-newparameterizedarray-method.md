---
title: ICorDebugEval2::NewParameterizedArray, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 14274932461fa7a5278c9a09b421f50be098cb91
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729661"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="b5bee-102">ICorDebugEval2::NewParameterizedArray, méthode</span><span class="sxs-lookup"><span data-stu-id="b5bee-102">ICorDebugEval2::NewParameterizedArray Method</span></span>

<span data-ttu-id="b5bee-103">Alloue un nouveau tableau du type d’élément et des dimensions spécifiés.</span><span class="sxs-lookup"><span data-stu-id="b5bee-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5bee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5bee-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5bee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5bee-105">Parameters</span></span>  

 `pElementType`  
 <span data-ttu-id="b5bee-106">dans Pointeur vers un objet ICorDebugType qui représente le type d’élément stocké dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="b5bee-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="b5bee-107">dans Nombre de dimensions du tableau.</span><span class="sxs-lookup"><span data-stu-id="b5bee-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="b5bee-108">Dans le .NET Framework version 2,0, cette valeur doit être 1.</span><span class="sxs-lookup"><span data-stu-id="b5bee-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="b5bee-109">dans Taille, en octets, de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="b5bee-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="b5bee-110">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5bee-110">[in] Optional.</span></span> <span data-ttu-id="b5bee-111">Limite inférieure de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="b5bee-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="b5bee-112">Si cette valeur est omise, une limite inférieure de zéro est utilisée pour chaque dimension.</span><span class="sxs-lookup"><span data-stu-id="b5bee-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5bee-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="b5bee-113">Remarks</span></span>  

 <span data-ttu-id="b5bee-114">Les éléments du tableau peuvent être des instances d’un type générique.</span><span class="sxs-lookup"><span data-stu-id="b5bee-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="b5bee-115">Le tableau est toujours créé dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b5bee-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="b5bee-116">Dans la .NET Framework 2,0, la valeur de `rank` doit être 1.</span><span class="sxs-lookup"><span data-stu-id="b5bee-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5bee-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5bee-117">Requirements</span></span>  

 <span data-ttu-id="b5bee-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5bee-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5bee-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5bee-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5bee-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5bee-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5bee-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5bee-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
