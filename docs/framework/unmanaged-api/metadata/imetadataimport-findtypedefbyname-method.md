---
title: IMetaDataImport::FindTypeDefByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: df1516a916b2b48080e4f94937fba063926330ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711297"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="09ba9-102">IMetaDataImport::FindTypeDefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="09ba9-102">IMetaDataImport::FindTypeDefByName Method</span></span>

<span data-ttu-id="09ba9-103">Obtient un pointeur vers le jeton de métadonnées TypeDef pour le <xref:System.Type> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="09ba9-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09ba9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09ba9-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09ba9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09ba9-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="09ba9-106">dans Nom du type pour lequel obtenir le jeton TypeDef.</span><span class="sxs-lookup"><span data-stu-id="09ba9-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="09ba9-107">dans Jeton TypeDef ou TypeRef représentant la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="09ba9-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="09ba9-108">Si le type à rechercher n’est pas une classe imbriquée, affectez-lui la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="09ba9-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="09ba9-109">à Pointeur vers le jeton TypeDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="09ba9-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ba9-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09ba9-110">Requirements</span></span>  

 <span data-ttu-id="09ba9-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ba9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ba9-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="09ba9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09ba9-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09ba9-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09ba9-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ba9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ba9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09ba9-115">See also</span></span>

- [<span data-ttu-id="09ba9-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="09ba9-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="09ba9-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="09ba9-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
