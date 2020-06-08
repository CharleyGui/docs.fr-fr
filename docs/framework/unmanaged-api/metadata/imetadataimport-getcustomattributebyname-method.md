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
ms.openlocfilehash: e6921a0f6420546ba1e866e37a7a7cb129a77c67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491457"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="05bf6-102">IMetaDataImport::GetCustomAttributeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="05bf6-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="05bf6-103">Obtient l’attribut personnalisé, en fonction de son nom et de son propriétaire.</span><span class="sxs-lookup"><span data-stu-id="05bf6-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05bf6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05bf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05bf6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05bf6-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="05bf6-106">dans Jeton de métadonnées représentant l’objet qui possède l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="05bf6-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="05bf6-107">dans Nom de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="05bf6-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="05bf6-108">à Pointeur vers un tableau de données qui est la valeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="05bf6-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="05bf6-109">à Taille en octets des données retournées dans \* `ppData` .</span><span class="sxs-lookup"><span data-stu-id="05bf6-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05bf6-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="05bf6-110">Remarks</span></span>  
 <span data-ttu-id="05bf6-111">Il est légal de définir plusieurs attributs personnalisés pour le même propriétaire ; ils peuvent même avoir le même nom.</span><span class="sxs-lookup"><span data-stu-id="05bf6-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="05bf6-112">Toutefois, `GetCustomAttributeByName` ne retourne qu’une seule instance.</span><span class="sxs-lookup"><span data-stu-id="05bf6-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="05bf6-113">( `GetCustomAttributeByName` retourne la première instance qu’il rencontre.) Pour rechercher toutes les instances d’un attribut personnalisé, appelez la méthode [IMetaDataImport :: EnumCustomAttributes (](imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="05bf6-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05bf6-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05bf6-114">Requirements</span></span>  
 <span data-ttu-id="05bf6-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05bf6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05bf6-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="05bf6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05bf6-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05bf6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05bf6-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05bf6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05bf6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05bf6-119">See also</span></span>

- [<span data-ttu-id="05bf6-120">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="05bf6-120">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="05bf6-121">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="05bf6-121">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
