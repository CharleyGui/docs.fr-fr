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
ms.openlocfilehash: 5485f43afe08fafa559d0418327a8f4f186860e7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491509"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="af25c-102">IMetaDataImport::FindTypeDefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="af25c-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="af25c-103">Obtient un pointeur vers le jeton de métadonnées TypeDef pour le <xref:System.Type> avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="af25c-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af25c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af25c-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af25c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="af25c-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="af25c-106">dans Nom du type pour lequel obtenir le jeton TypeDef.</span><span class="sxs-lookup"><span data-stu-id="af25c-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="af25c-107">dans Jeton TypeDef ou TypeRef représentant la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="af25c-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="af25c-108">Si le type à rechercher n’est pas une classe imbriquée, affectez-lui la valeur NULL.</span><span class="sxs-lookup"><span data-stu-id="af25c-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="af25c-109">à Pointeur vers le jeton TypeDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="af25c-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af25c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af25c-110">Requirements</span></span>  
 <span data-ttu-id="af25c-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af25c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af25c-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="af25c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af25c-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="af25c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af25c-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af25c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af25c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af25c-115">See also</span></span>

- [<span data-ttu-id="af25c-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="af25c-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="af25c-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="af25c-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
