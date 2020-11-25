---
title: IMetaDataImport::GetClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 5a442d8d0916b0e86f25c03507de66fc999f2159
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711258"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="b8342-102">IMetaDataImport::GetClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="b8342-102">IMetaDataImport::GetClassLayout Method</span></span>

<span data-ttu-id="b8342-103">Obtient les informations de disposition pour la classe référencée par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8342-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8342-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8342-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8342-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8342-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="b8342-106">dans Jeton TypeDef pour la classe avec la disposition à retourner.</span><span class="sxs-lookup"><span data-stu-id="b8342-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="b8342-107">à L’une des valeurs 1, 2, 4, 8 ou 16, représentant la taille de Pack de la classe.</span><span class="sxs-lookup"><span data-stu-id="b8342-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="b8342-108">à Tableau de valeurs [COR_FIELD_OFFSET](cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="b8342-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b8342-109">[in] Taille maximale du tableau `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="b8342-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="b8342-110">à Nombre d’éléments retournés dans `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="b8342-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="b8342-111">à Taille en octets de la classe représentée par `td` .</span><span class="sxs-lookup"><span data-stu-id="b8342-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8342-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8342-112">Requirements</span></span>  

 <span data-ttu-id="b8342-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8342-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8342-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b8342-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8342-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8342-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8342-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8342-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8342-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8342-117">See also</span></span>

- [<span data-ttu-id="b8342-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b8342-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b8342-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b8342-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
