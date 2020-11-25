---
title: IMetaDataImport2::GetGenericParamConstraintProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
ms.openlocfilehash: 8beaea0b7493b7cea76466bb15355cfc5c6d5c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702704"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a><span data-ttu-id="c696a-102">IMetaDataImport2::GetGenericParamConstraintProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c696a-102">IMetaDataImport2::GetGenericParamConstraintProps Method</span></span>

<span data-ttu-id="c696a-103">Obtient les métadonnées associées à la contrainte de paramètre générique représentée par le jeton de contrainte spécifié.</span><span class="sxs-lookup"><span data-stu-id="c696a-103">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c696a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c696a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c696a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c696a-105">Parameters</span></span>  

 `gpc`  
 <span data-ttu-id="c696a-106">dans Jeton de la contrainte de paramètre générique pour laquelle retourner les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c696a-106">[in] The token to the generic parameter constraint for which to return the metadata.</span></span>  
  
 `ptGenericParam`  
 <span data-ttu-id="c696a-107">à Pointeur vers le jeton qui représente le paramètre générique qui est imposé.</span><span class="sxs-lookup"><span data-stu-id="c696a-107">[out] A pointer to the token that represents the generic parameter that is constrained.</span></span>  
  
 `ptkConstraintType`  
 <span data-ttu-id="c696a-108">à Pointeur vers un jeton TypeDef, TypeRef ou TypeSpec qui représente une contrainte sur `ptGenericParam` .</span><span class="sxs-lookup"><span data-stu-id="c696a-108">[out] A pointer to a TypeDef, TypeRef, or TypeSpec token that represents a constraint on `ptGenericParam`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c696a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c696a-109">Requirements</span></span>  

 <span data-ttu-id="c696a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c696a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c696a-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c696a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c696a-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c696a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c696a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c696a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c696a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c696a-114">See also</span></span>

- [<span data-ttu-id="c696a-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c696a-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="c696a-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c696a-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
