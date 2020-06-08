---
title: IMetaDataImport::IsValidToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.IsValidToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::IsValidToken
helpviewer_keywords:
- IMetaDataImport::IsValidToken method [.NET Framework metadata]
- IsValidToken method [.NET Framework metadata]
ms.assetid: aeb0fc63-9eff-4384-9284-cb9900572d74
topic_type:
- apiref
ms.openlocfilehash: 9190d021b801be951d214406dde7e6d76da15608
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503436"
---
# <a name="imetadataimportisvalidtoken-method"></a><span data-ttu-id="d17c2-102">IMetaDataImport::IsValidToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d17c2-102">IMetaDataImport::IsValidToken Method</span></span>
<span data-ttu-id="d17c2-103">Obtient une valeur indiquant si le jeton spécifié contient une référence valide à un objet de code.</span><span class="sxs-lookup"><span data-stu-id="d17c2-103">Gets a value indicating whether the specified token holds a valid reference to a code object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d17c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d17c2-104">Syntax</span></span>  
  
```cpp  
BOOL IsValidToken (  
   [in] mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d17c2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d17c2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d17c2-106">dans Jeton pour lequel vérifier la validité de la référence.</span><span class="sxs-lookup"><span data-stu-id="d17c2-106">[in] The token to check the reference validity for.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d17c2-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d17c2-107">Return Value</span></span>  
 <span data-ttu-id="d17c2-108">`true`Si `tk` est un jeton de métadonnées valide dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="d17c2-108">`true` if `tk` is a valid metadata token within the current scope.</span></span> <span data-ttu-id="d17c2-109">Sinon, valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="d17c2-109">Otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d17c2-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d17c2-110">Requirements</span></span>  
 <span data-ttu-id="d17c2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d17c2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d17c2-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d17c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d17c2-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d17c2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d17c2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d17c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17c2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d17c2-115">See also</span></span>

- [<span data-ttu-id="d17c2-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d17c2-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d17c2-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d17c2-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
