---
title: IMetaDataImport::GetTypeDefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 9dd973fe3e0802c49c220db51a21c223730e5aec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729162"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="c440e-102">IMetaDataImport::GetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c440e-102">IMetaDataImport::GetTypeDefProps Method</span></span>

<span data-ttu-id="c440e-103">Retourne des informations de métadonnées pour le <xref:System.Type> représenté par le jeton Typedef spécifié.</span><span class="sxs-lookup"><span data-stu-id="c440e-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c440e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c440e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c440e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c440e-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="c440e-106">dans Jeton TypeDef qui représente le type pour lequel retourner des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c440e-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="c440e-107">à Mémoire tampon contenant le nom de type.</span><span class="sxs-lookup"><span data-stu-id="c440e-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="c440e-108">dans Taille en caractères larges de `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="c440e-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="c440e-109">à Nombre de caractères larges retournés dans `szTypeDef` .</span><span class="sxs-lookup"><span data-stu-id="c440e-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="c440e-110">à Pointeur vers tous les indicateurs qui modifient la définition du type.</span><span class="sxs-lookup"><span data-stu-id="c440e-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="c440e-111">Cette valeur est un masque de masque de l’énumération [CorTypeAttr](cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c440e-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="c440e-112">à Jeton de métadonnées TypeDef ou TypeRef qui représente le type de base du type demandé.</span><span class="sxs-lookup"><span data-stu-id="c440e-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c440e-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c440e-113">Requirements</span></span>  

 <span data-ttu-id="c440e-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c440e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c440e-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c440e-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c440e-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c440e-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c440e-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c440e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c440e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c440e-118">See also</span></span>

- [<span data-ttu-id="c440e-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c440e-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c440e-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c440e-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
