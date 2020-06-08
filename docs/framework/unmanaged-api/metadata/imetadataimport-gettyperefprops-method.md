---
title: IMetaDataImport::GetTypeRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 273922e00c3e5319d5a03652cc77b69f4479ea67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503521"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="b110f-102">IMetaDataImport::GetTypeRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b110f-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="b110f-103">Obtient les métadonnées associées à la <xref:System.Type> référencée par le jeton TypeRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="b110f-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b110f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b110f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b110f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b110f-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="b110f-106">dans Jeton TypeRef qui représente le type pour lequel retourner des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b110f-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="b110f-107">à Pointeur vers l’étendue dans laquelle la référence est effectuée.</span><span class="sxs-lookup"><span data-stu-id="b110f-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="b110f-108">Cette valeur est un jeton AssemblyRef ou ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="b110f-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="b110f-109">à Mémoire tampon contenant le nom de type.</span><span class="sxs-lookup"><span data-stu-id="b110f-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b110f-110">dans Taille demandée en caractères larges de `szName` .</span><span class="sxs-lookup"><span data-stu-id="b110f-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b110f-111">à Taille retournée en caractères larges de `szName` .</span><span class="sxs-lookup"><span data-stu-id="b110f-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b110f-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b110f-112">Requirements</span></span>  
 <span data-ttu-id="b110f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b110f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b110f-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b110f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b110f-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b110f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b110f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b110f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b110f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b110f-117">See also</span></span>

- [<span data-ttu-id="b110f-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b110f-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b110f-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b110f-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
