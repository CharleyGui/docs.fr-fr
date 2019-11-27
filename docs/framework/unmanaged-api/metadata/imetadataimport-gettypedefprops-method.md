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
ms.openlocfilehash: c9ac624e17223def206e86fd92ee4fd2de7f6082
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436748"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="dcbce-102">IMetaDataImport::GetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="dcbce-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="dcbce-103">Retourne des informations de métadonnées pour le <xref:System.Type> représenté par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="dcbce-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcbce-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dcbce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dcbce-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dcbce-106">dans Jeton TypeDef qui représente le type pour lequel retourner des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="dcbce-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="dcbce-107">à Mémoire tampon contenant le nom de type.</span><span class="sxs-lookup"><span data-stu-id="dcbce-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="dcbce-108">dans Taille en caractères larges de `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="dcbce-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="dcbce-109">à Nombre de caractères larges retournés dans `szTypeDef`.</span><span class="sxs-lookup"><span data-stu-id="dcbce-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="dcbce-110">à Pointeur vers tous les indicateurs qui modifient la définition du type.</span><span class="sxs-lookup"><span data-stu-id="dcbce-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="dcbce-111">Cette valeur est un masque de masque de l’énumération [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="dcbce-111">This value is a bitmask from the [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="dcbce-112">à Jeton de métadonnées TypeDef ou TypeRef qui représente le type de base du type demandé.</span><span class="sxs-lookup"><span data-stu-id="dcbce-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbce-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dcbce-113">Requirements</span></span>  
 <span data-ttu-id="dcbce-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcbce-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcbce-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dcbce-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcbce-116">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dcbce-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcbce-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcbce-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbce-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcbce-118">See also</span></span>

- [<span data-ttu-id="dcbce-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="dcbce-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="dcbce-120">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="dcbce-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
