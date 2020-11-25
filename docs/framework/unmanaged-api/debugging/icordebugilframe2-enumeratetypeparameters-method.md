---
title: ICorDebugILFrame2::EnumerateTypeParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugILFrame2 interface [.NET Framework debugging]
- ICorDebugILFrame2::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 722d0d74-e0df-491f-98c4-62d501dfaf6f
topic_type:
- apiref
ms.openlocfilehash: 73c17864047270302dbc115667eec4bf5ea1569d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725040"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="69625-102">ICorDebugILFrame2::EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="69625-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>

<span data-ttu-id="69625-103">Obtient un objet ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de ce frame.</span><span class="sxs-lookup"><span data-stu-id="69625-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69625-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69625-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69625-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69625-105">Parameters</span></span>  

 `ppTyParEnum`  
 <span data-ttu-id="69625-106">Pointeur vers l’adresse d’un objet d’interface ICorDebugTypeEnum qui autorise l’énumération des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="69625-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="69625-107">La liste des paramètres de type inclut les paramètres de type de classe (le cas échéant) suivis des paramètres de type de méthode (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="69625-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69625-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="69625-108">Remarks</span></span>  

 <span data-ttu-id="69625-109">Utilisez la méthode [IMetaDataImport2 :: EnumGenericParams,](../metadata/imetadataimport2-enumgenericparams-method.md) pour déterminer le nombre de paramètres de type de classe et de paramètres de type de méthode que cette liste contient.</span><span class="sxs-lookup"><span data-stu-id="69625-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="69625-110">Les paramètres de type ne sont pas toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="69625-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69625-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69625-111">Requirements</span></span>  

 <span data-ttu-id="69625-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69625-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69625-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69625-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69625-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69625-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69625-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69625-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
