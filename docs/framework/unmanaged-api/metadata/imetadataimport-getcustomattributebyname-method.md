---
title: IMetaDataImport::GetCustomAttributeByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bebf254110d9970ff3a99f948ff2e831ffb6b35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782435"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="49e53-102">IMetaDataImport::GetCustomAttributeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="49e53-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="49e53-103">Obtient l’attribut personnalisé, en fonction de son nom et le propriétaire.</span><span class="sxs-lookup"><span data-stu-id="49e53-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e53-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49e53-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49e53-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="49e53-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="49e53-106">[in] Un jeton de métadonnées représentant l’objet qui possède l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="49e53-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="49e53-107">[in] Le nom de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="49e53-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="49e53-108">[out] Pointeur vers un tableau de données qui est la valeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="49e53-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="49e53-109">[out] La taille en octets des données retournées dans \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="49e53-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49e53-110">Notes</span><span class="sxs-lookup"><span data-stu-id="49e53-110">Remarks</span></span>  
 <span data-ttu-id="49e53-111">Il est permis de définir plusieurs attributs personnalisés pour le même propriétaire ; ceux-ci peuvent même avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="49e53-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="49e53-112">Toutefois, `GetCustomAttributeByName` ne retourne qu’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="49e53-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="49e53-113">(`GetCustomAttributeByName` retourne la première instance qu’il rencontre.) Pour rechercher toutes les instances d’un attribut personnalisé, appelez le [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="49e53-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49e53-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49e53-114">Requirements</span></span>  
 <span data-ttu-id="49e53-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49e53-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e53-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="49e53-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="49e53-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49e53-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="49e53-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49e53-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e53-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49e53-119">See also</span></span>

- [<span data-ttu-id="49e53-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="49e53-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="49e53-121">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="49e53-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
