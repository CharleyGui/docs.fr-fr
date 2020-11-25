---
title: IMetaDataImport::EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 3b12200dae23a7b6a2f6e1654e46fdf74dc90968
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700533"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="5e947-102">IMetaDataImport::EnumCustomAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="5e947-102">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="5e947-103">Énumère les jetons de définition d’attribut personnalisés associés au type ou au membre spécifié.</span><span class="sxs-lookup"><span data-stu-id="5e947-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e947-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e947-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e947-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e947-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="5e947-106">[in, out] Pointeur vers l’énumérateur retourné.</span><span class="sxs-lookup"><span data-stu-id="5e947-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="5e947-107">dans Jeton pour la portée de l’énumération, ou zéro pour tous les attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="5e947-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="5e947-108">dans Jeton pour le constructeur du type des attributs à énumérer, ou `null` pour tous les types.</span><span class="sxs-lookup"><span data-stu-id="5e947-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="5e947-109">à Tableau de jetons d’attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="5e947-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5e947-110">[in] Taille maximale du tableau `rCustomAttributes`.</span><span class="sxs-lookup"><span data-stu-id="5e947-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="5e947-111">[out, optional] Nombre réel de valeurs de jeton retournées dans `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="5e947-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e947-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="5e947-112">Return Value</span></span>  
  
|<span data-ttu-id="5e947-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e947-113">HRESULT</span></span>|<span data-ttu-id="5e947-114">Description</span><span class="sxs-lookup"><span data-stu-id="5e947-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5e947-115">`EnumCustomAttributes` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5e947-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5e947-116">Il n’existe aucun attribut personnalisé à énumérer.</span><span class="sxs-lookup"><span data-stu-id="5e947-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="5e947-117">Dans ce cas, `pcCustomAttributes` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="5e947-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e947-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e947-118">Requirements</span></span>  

 <span data-ttu-id="5e947-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e947-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e947-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5e947-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e947-121">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5e947-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e947-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e947-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e947-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e947-123">See also</span></span>

- [<span data-ttu-id="5e947-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="5e947-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5e947-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="5e947-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
