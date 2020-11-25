---
title: IMetaDataImport2::GetGenericParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: 16f69d571ffed87a2e848124ce16ac942d319c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702678"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="bc2d4-102">IMetaDataImport2::GetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="bc2d4-102">IMetaDataImport2::GetGenericParamProps Method</span></span>

<span data-ttu-id="bc2d4-103">Obtient les métadonnées associées au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc2d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc2d4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc2d4-105">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="bc2d4-106">dans Jeton qui représente le paramètre générique pour lequel retourner des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="bc2d4-107">à Position ordinale du `Type` paramètre dans le constructeur parent ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="bc2d4-108">à Valeur de l’énumération [CorGenericParamAttr,](corgenericparamattr-enumeration.md) qui décrit le `Type` pour le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-108">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="bc2d4-109">à Jeton TypeDef ou MethodDef qui représente le propriétaire du paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="bc2d4-110">à Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="bc2d4-111">à Nom du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bc2d4-112">dans Taille de la `wzName` mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bc2d4-113">à Taille retournée du nom, en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="bc2d4-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc2d4-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bc2d4-114">Requirements</span></span>  

 <span data-ttu-id="bc2d4-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2d4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2d4-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bc2d4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc2d4-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc2d4-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc2d4-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2d4-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc2d4-119">See also</span></span>

- [<span data-ttu-id="bc2d4-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="bc2d4-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="bc2d4-121">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="bc2d4-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
