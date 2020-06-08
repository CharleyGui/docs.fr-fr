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
ms.openlocfilehash: 5de62db4180a6a9160193053fe42e39cebc34d0e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492475"
---
# <a name="imetadataimportcloseenum-method"></a><span data-ttu-id="b9755-102">IMetaDataImport::CloseEnum, méthode</span><span class="sxs-lookup"><span data-stu-id="b9755-102">IMetaDataImport::CloseEnum Method</span></span>
<span data-ttu-id="b9755-103">Ferme l’énumérateur identifié par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9755-103">Closes the enumerator that is identified by the specified handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9755-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9755-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
   [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9755-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9755-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="b9755-106">dans Handle de l’énumérateur à fermer.</span><span class="sxs-lookup"><span data-stu-id="b9755-106">[in] The handle for the enumerator to close.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9755-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="b9755-107">Remarks</span></span>  
 <span data-ttu-id="b9755-108">Le handle spécifié par `hEnum` est obtenu à partir d’un appel de `Enum` *nom* précédent (par exemple, [IMetaDataImport :: EnumTypeDefs,](imetadataimport-enumtypedefs-method.md)).</span><span class="sxs-lookup"><span data-stu-id="b9755-108">The handle specified by `hEnum` is obtained from a previous `Enum`*Name* call (for example, [IMetaDataImport::EnumTypeDefs](imetadataimport-enumtypedefs-method.md)).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9755-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9755-109">Requirements</span></span>  
 <span data-ttu-id="b9755-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9755-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9755-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9755-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9755-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9755-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9755-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9755-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9755-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9755-114">See also</span></span>

- [<span data-ttu-id="b9755-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b9755-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b9755-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b9755-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
