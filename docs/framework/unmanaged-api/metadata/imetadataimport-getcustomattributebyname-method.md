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
ms.openlocfilehash: bd7ba7ff10918e5953ea8ae89a60af3115af48a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437685"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="99cdd-102">IMetaDataImport::GetCustomAttributeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="99cdd-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="99cdd-103">Obtient l’attribut personnalisé, en fonction de son nom et de son propriétaire.</span><span class="sxs-lookup"><span data-stu-id="99cdd-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99cdd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99cdd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99cdd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99cdd-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="99cdd-106">dans Jeton de métadonnées représentant l’objet qui possède l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99cdd-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="99cdd-107">dans Nom de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99cdd-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="99cdd-108">à Pointeur vers un tableau de données qui est la valeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="99cdd-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="99cdd-109">à Taille en octets des données retournées dans \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="99cdd-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99cdd-110">Notes</span><span class="sxs-lookup"><span data-stu-id="99cdd-110">Remarks</span></span>  
 <span data-ttu-id="99cdd-111">Il est légal de définir plusieurs attributs personnalisés pour le même propriétaire ; ils peuvent même avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="99cdd-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="99cdd-112">Toutefois, `GetCustomAttributeByName` ne retourne qu’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="99cdd-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="99cdd-113">(`GetCustomAttributeByName` retourne la première instance qu’il rencontre.) Pour rechercher toutes les instances d’un attribut personnalisé, appelez la méthode [IMetaDataImport :: EnumCustomAttributes (](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99cdd-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99cdd-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="99cdd-114">Requirements</span></span>  
 <span data-ttu-id="99cdd-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99cdd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99cdd-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="99cdd-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99cdd-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="99cdd-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99cdd-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99cdd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99cdd-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99cdd-119">See also</span></span>

- [<span data-ttu-id="99cdd-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="99cdd-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="99cdd-121">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="99cdd-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
