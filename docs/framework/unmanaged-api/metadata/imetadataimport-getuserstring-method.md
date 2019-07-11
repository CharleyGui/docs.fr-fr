---
title: IMetaDataImport::GetUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: edeaefd0792a5cc03ae6d4385ff669a343ffdfc9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778807"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="3eb82-102">IMetaDataImport::GetUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="3eb82-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="3eb82-103">Obtient la chaîne littérale représentée par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="3eb82-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eb82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3eb82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3eb82-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3eb82-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="3eb82-106">[in] Le jeton de chaîne pour retourner la chaîne associée.</span><span class="sxs-lookup"><span data-stu-id="3eb82-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="3eb82-107">[out] Une copie de la chaîne demandée.</span><span class="sxs-lookup"><span data-stu-id="3eb82-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="3eb82-108">[in] La taille maximale en caractères larges de demandé `szString`.</span><span class="sxs-lookup"><span data-stu-id="3eb82-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="3eb82-109">[out] La taille en caractères larges de retourné `szString`.</span><span class="sxs-lookup"><span data-stu-id="3eb82-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3eb82-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3eb82-110">Requirements</span></span>  
 <span data-ttu-id="3eb82-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eb82-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eb82-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3eb82-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3eb82-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3eb82-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3eb82-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eb82-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eb82-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3eb82-115">See also</span></span>

- [<span data-ttu-id="3eb82-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3eb82-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3eb82-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="3eb82-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
