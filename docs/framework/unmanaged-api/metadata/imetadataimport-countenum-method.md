---
title: IMetaDataImport::CountEnum, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CountEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CountEnum
helpviewer_keywords:
- CountEnum method [.NET Framework metadata]
- IMetaDataImport::CountEnum method [.NET Framework metadata]
ms.assetid: d1de53ad-9435-4b5f-9df7-07f21210e5b5
topic_type:
- apiref
ms.openlocfilehash: 4521a3f15ec358a4d786a4533efb6b99d0e1c1cc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492380"
---
# <a name="imetadataimportcountenum-method"></a><span data-ttu-id="6af04-102">IMetaDataImport::CountEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="6af04-102">IMetaDataImport::CountEnum Method</span></span>
<span data-ttu-id="6af04-103">Obtient le nombre d’éléments de l’énumération récupérés par l’énumérateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="6af04-103">Gets the number of elements in the enumeration that was retrieved by the specified enumerator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6af04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6af04-104">Syntax</span></span>  
  
```cpp  
HRESULT CountEnum (  
   [in]  HCORENUM    hEnum,
   [out] ULONG       *pulCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6af04-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6af04-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="6af04-106">dans Handle de l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="6af04-106">[in] The handle for the enumerator.</span></span>  
  
 `pulCount`  
 <span data-ttu-id="6af04-107">à Nombre d’éléments énumérés.</span><span class="sxs-lookup"><span data-stu-id="6af04-107">[out] The number of elements enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6af04-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="6af04-108">Remarks</span></span>  
 <span data-ttu-id="6af04-109">Le handle spécifié par `hEnum` est obtenu à partir d’un appel de `Enum` *nom* précédent (par exemple, [IMetaDataImport :: EnumTypeDefs,](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="6af04-109">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6af04-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6af04-110">Requirements</span></span>  
 <span data-ttu-id="6af04-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6af04-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6af04-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6af04-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6af04-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6af04-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6af04-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6af04-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6af04-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6af04-115">See also</span></span>

- [<span data-ttu-id="6af04-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6af04-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6af04-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6af04-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
