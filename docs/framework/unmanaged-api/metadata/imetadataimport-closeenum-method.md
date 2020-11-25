---
title: IMetaDataImport::CloseEnum, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::CloseEnum
helpviewer_keywords:
- IMetaDataImport::CloseEnum method [.NET Framework metadata]
- CloseEnum method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 727819d5-1dab-4ebb-ac25-950b4111dc72
topic_type:
- apiref
ms.openlocfilehash: f418b48f1b62ae8093197d64ca44b2ef659990a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701716"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="da4c3-102">IMetaDataImport::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="da4c3-102">IMetaDataImport::CloseEnum Method</span></span>

<span data-ttu-id="da4c3-103">Ferme l’énumérateur identifié par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="da4c3-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da4c3-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da4c3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da4c3-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="da4c3-106">dans Handle de l’énumérateur à fermer.</span><span class="sxs-lookup"><span data-stu-id="da4c3-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da4c3-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="da4c3-107">Remarks</span></span>  

 <span data-ttu-id="da4c3-108">Le handle spécifié par `hEnum` est obtenu à partir d’un appel de `Enum` *nom* précédent (par exemple, [IMetaDataImport :: EnumTypeDefs,](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="da4c3-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4c3-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da4c3-109">Requirements</span></span>  

 <span data-ttu-id="da4c3-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da4c3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4c3-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="da4c3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da4c3-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da4c3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da4c3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da4c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4c3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da4c3-114">See also</span></span>

- [<span data-ttu-id="da4c3-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="da4c3-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="da4c3-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="da4c3-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
