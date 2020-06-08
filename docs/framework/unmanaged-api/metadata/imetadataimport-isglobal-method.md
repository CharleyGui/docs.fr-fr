---
title: IMetaDataImport::IsGlobal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsGlobal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsGlobal
helpviewer_keywords:
- IsGlobal method [.NET Framework metadata]
- IMetaDataImport::IsGlobal method [.NET Framework metadata]
ms.assetid: 44cf6908-f555-4ae8-b2cf-24bd974bf2fe
topic_type:
- apiref
ms.openlocfilehash: d477976952d2c1875a620d1397fd43e5c5e2836f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503469"
---
# <a name="imetadataimportisglobal-method"></a><span data-ttu-id="56657-102">IMetaDataImport::IsGlobal, méthode</span><span class="sxs-lookup"><span data-stu-id="56657-102">IMetaDataImport::IsGlobal Method</span></span>
<span data-ttu-id="56657-103">Obtient une valeur qui indique si le champ, la méthode ou le type représenté(e) par le jeton de métadonnées spécifié a une portée globale.</span><span class="sxs-lookup"><span data-stu-id="56657-103">Gets a value indicating whether the field, method, or type represented by the specified metadata token has global scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56657-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56657-104">Syntax</span></span>  
  
```cpp  
HRESULT IsGlobal (  
   [in]  mdToken     pd,  
   [out] int         *pbGlobal  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56657-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56657-105">Parameters</span></span>  
 `pd`  
 <span data-ttu-id="56657-106">dans Jeton de métadonnées qui représente un type, un champ ou une méthode.</span><span class="sxs-lookup"><span data-stu-id="56657-106">[in] A metadata token that represents a type, field, or method.</span></span>  
  
 `pbGlobal`  
 <span data-ttu-id="56657-107">[out] 1 si l’objet a une portée globale ; Sinon, 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="56657-107">[out] 1 if the object has global scope; otherwise, 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56657-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56657-108">Requirements</span></span>  
 <span data-ttu-id="56657-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56657-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56657-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56657-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56657-111">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56657-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56657-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56657-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56657-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56657-113">See also</span></span>

- [<span data-ttu-id="56657-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="56657-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="56657-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="56657-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
