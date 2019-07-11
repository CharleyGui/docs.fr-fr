---
title: IMetaDataImport::GetCustomAttributeProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c714915651d8660a739d8ee6518fc3814af4c08d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782413"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a><span data-ttu-id="8db2e-102">IMetaDataImport::GetCustomAttributeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8db2e-102">IMetaDataImport::GetCustomAttributeProps Method</span></span>
<span data-ttu-id="8db2e-103">Obtient la valeur de l'attribut personnalisé, en fonction de son jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8db2e-103">Gets the value of the custom attribute, given its metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8db2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8db2e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8db2e-105">Parameters</span></span>  
 `cv`  
 <span data-ttu-id="8db2e-106">[in] Jeton de métadonnées représentant l'attribut personnalisé à récupérer.</span><span class="sxs-lookup"><span data-stu-id="8db2e-106">[in] A metadata token that represents the custom attribute to be retrieved.</span></span>  
  
 `ptkObj`  
 <span data-ttu-id="8db2e-107">[out, optional] Jeton de métadonnées représentant l'objet que l'attribut personnalisé modifie.</span><span class="sxs-lookup"><span data-stu-id="8db2e-107">[out, optional] A metadata token representing the object that the custom attribute modifies.</span></span> <span data-ttu-id="8db2e-108">Cette valeur peut correspondre à tout type de jeton de métadonnées, à l'exception de `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="8db2e-108">This value can be any type of metadata token except `mdCustomAttribute`.</span></span>  
  
 `ptkType`  
 <span data-ttu-id="8db2e-109">[out, optional] Jeton de métadonnées `mdMethodDef` ou `mdMemberRef` représentant le <xref:System.Type> de l'attribut personnalisé retourné.</span><span class="sxs-lookup"><span data-stu-id="8db2e-109">[out, optional] An `mdMethodDef` or `mdMemberRef` metadata token representing the <xref:System.Type> of the returned custom attribute.</span></span>  
  
 `ppBlob`  
 <span data-ttu-id="8db2e-110">[out, optional] Pointeur vers un tableau de données correspondant à la valeur de l'attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8db2e-110">[out, optional] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="8db2e-111">[out, optional] Taille en octets des données retournées dans \*`ppBlob`.</span><span class="sxs-lookup"><span data-stu-id="8db2e-111">[out, optional] The size in bytes of the data returned in \*`ppBlob`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8db2e-112">Notes</span><span class="sxs-lookup"><span data-stu-id="8db2e-112">Remarks</span></span>  
 <span data-ttu-id="8db2e-113">Un attribut personnalisé est stocké sous forme d'un tableau de données, le format qui est compris par le moteur de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8db2e-113">A custom attribute is stored as an array of data, the format which is understood by the metadata engine.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db2e-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8db2e-114">Requirements</span></span>  
 <span data-ttu-id="8db2e-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8db2e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8db2e-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8db2e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8db2e-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8db2e-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8db2e-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8db2e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db2e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8db2e-119">See also</span></span>

- [<span data-ttu-id="8db2e-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8db2e-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8db2e-121">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8db2e-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
