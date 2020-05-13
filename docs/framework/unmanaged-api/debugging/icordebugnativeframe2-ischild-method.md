---
title: ICorDebugNativeFrame2::IsChild, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
ms.openlocfilehash: 759ba7bd46f8231143e743aa5ffcabffeb99c3b6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205109"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="d4834-102">ICorDebugNativeFrame2::IsChild, méthode</span><span class="sxs-lookup"><span data-stu-id="d4834-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="d4834-103">Détermine si le frame actuel est un Frame enfant.</span><span class="sxs-lookup"><span data-stu-id="d4834-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4834-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4834-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4834-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4834-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="d4834-106">à Valeur booléenne qui spécifie si le frame actuel est un Frame enfant.</span><span class="sxs-lookup"><span data-stu-id="d4834-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4834-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d4834-107">Return Value</span></span>  
 <span data-ttu-id="d4834-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d4834-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d4834-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4834-109">HRESULT</span></span>|<span data-ttu-id="d4834-110">Description</span><span class="sxs-lookup"><span data-stu-id="d4834-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4834-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4834-111">S_OK</span></span>|<span data-ttu-id="d4834-112">L’état de l’enfant a été retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d4834-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="d4834-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d4834-113">E_FAIL</span></span>|<span data-ttu-id="d4834-114">L’état de l’enfant n’a pas pu être retourné.</span><span class="sxs-lookup"><span data-stu-id="d4834-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="d4834-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d4834-115">E_INVALIDARG</span></span>|<span data-ttu-id="d4834-116">`pIsChild` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="d4834-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d4834-117">Exceptions</span><span class="sxs-lookup"><span data-stu-id="d4834-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4834-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4834-118">Remarks</span></span>  
 <span data-ttu-id="d4834-119">La `IsChild` méthode retourne `true` si l’objet Frame sur lequel vous appelez la méthode est un enfant d’un autre Frame.</span><span class="sxs-lookup"><span data-stu-id="d4834-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="d4834-120">Si c’est le cas, utilisez la méthode [IsMatchingParentFrame,](icordebugnativeframe2-ismatchingparentframe-method.md) pour vérifier si un frame est son parent.</span><span class="sxs-lookup"><span data-stu-id="d4834-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4834-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4834-121">Requirements</span></span>  
 <span data-ttu-id="d4834-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4834-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4834-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4834-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4834-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4834-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4834-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4834-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4834-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4834-126">See also</span></span>

- [<span data-ttu-id="d4834-127">ICorDebugNativeFrame2, interface</span><span class="sxs-lookup"><span data-stu-id="d4834-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="d4834-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d4834-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d4834-129">Débogage</span><span class="sxs-lookup"><span data-stu-id="d4834-129">Debugging</span></span>](index.md)
