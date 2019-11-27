---
title: IMetaDataImport::GetNameFromToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437263"
---
# <a name="imetadataimportgetnamefromtoken-method"></a><span data-ttu-id="b64f6-102">IMetaDataImport::GetNameFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="b64f6-102">IMetaDataImport::GetNameFromToken Method</span></span>
<span data-ttu-id="b64f6-103">Obtient le nom UTF-8 de l'objet référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="b64f6-103">Gets the UTF-8 name of the object referenced by the specified metadata token.</span></span> <span data-ttu-id="b64f6-104">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="b64f6-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b64f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b64f6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b64f6-106">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b64f6-107">dans Jeton représentant l’objet pour lequel le nom doit être retourné.</span><span class="sxs-lookup"><span data-stu-id="b64f6-107">[in] The token representing the object to return the name for.</span></span>  
  
 `pszUtf8NamePtr`  
 <span data-ttu-id="b64f6-108">à Pointeur vers le nom d’objet UTF-8 dans le tas.</span><span class="sxs-lookup"><span data-stu-id="b64f6-108">[out] A pointer to the UTF-8 object name in the heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64f6-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b64f6-109">Remarks</span></span>  
 <span data-ttu-id="b64f6-110">`GetNameFromToken` est obsolète.</span><span class="sxs-lookup"><span data-stu-id="b64f6-110">`GetNameFromToken` is obsolete.</span></span> <span data-ttu-id="b64f6-111">Vous pouvez également appeler une méthode pour obtenir les propriétés du type particulier de jeton requis, par exemple `GetFieldProps` pour un champ ou un `GetMethodProps` pour une méthode.</span><span class="sxs-lookup"><span data-stu-id="b64f6-111">As an alternative, call a method to get the properties of the particular type of token required, such as `GetFieldProps` for a field or `GetMethodProps` for a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64f6-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b64f6-112">Requirements</span></span>  
 <span data-ttu-id="b64f6-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b64f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64f6-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b64f6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b64f6-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b64f6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b64f6-116">**Versions de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="b64f6-116">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64f6-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b64f6-117">See also</span></span>

- [<span data-ttu-id="b64f6-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b64f6-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b64f6-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b64f6-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
