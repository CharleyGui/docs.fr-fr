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
ms.openlocfilehash: 9020fed83b1c57cae3cc492872a279afb0195983
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205173"
---
# <a name="icordebugilframe2enumeratetypeparameters-method"></a><span data-ttu-id="0b8b6-102">ICorDebugILFrame2::EnumerateTypeParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="0b8b6-102">ICorDebugILFrame2::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="0b8b6-103">Obtient un objet ICorDebugTypeEnum qui contient les <xref:System.Type> paramètres de ce frame.</span><span class="sxs-lookup"><span data-stu-id="0b8b6-103">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b8b6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum    **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b8b6-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="0b8b6-106">Pointeur vers l’adresse d’un objet d’interface ICorDebugTypeEnum qui autorise l’énumération des paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="0b8b6-106">A pointer to the address of a ICorDebugTypeEnum interface object that allows enumeration of type parameters.</span></span>  
  
 <span data-ttu-id="0b8b6-107">La liste des paramètres de type inclut les paramètres de type de classe (le cas échéant) suivis des paramètres de type de méthode (le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="0b8b6-107">The list of type parameters include the class type parameters (if any) followed by the method type parameters (if any).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b8b6-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b8b6-108">Remarks</span></span>  
 <span data-ttu-id="0b8b6-109">Utilisez la méthode [IMetaDataImport2 :: EnumGenericParams,](../metadata/imetadataimport2-enumgenericparams-method.md) pour déterminer le nombre de paramètres de type de classe et de paramètres de type de méthode que cette liste contient.</span><span class="sxs-lookup"><span data-stu-id="0b8b6-109">Use the [IMetaDataImport2::EnumGenericParams](../metadata/imetadataimport2-enumgenericparams-method.md) method to determine how many class type parameters and method type parameters this list contains.</span></span>  
  
 <span data-ttu-id="0b8b6-110">Les paramètres de type ne sont pas toujours disponibles.</span><span class="sxs-lookup"><span data-stu-id="0b8b6-110">The type parameters are not always available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8b6-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0b8b6-111">Requirements</span></span>  
 <span data-ttu-id="0b8b6-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b8b6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8b6-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b8b6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b8b6-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b8b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b8b6-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
