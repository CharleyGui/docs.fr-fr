---
title: IMetaDataImport::EnumModuleRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: fe7350e6d8e400ae37b5b8b7854a56f3c5c53ea7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491745"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="c0567-102">IMetaDataImport::EnumModuleRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="c0567-102">IMetaDataImport::EnumModuleRefs Method</span></span>
<span data-ttu-id="c0567-103">Énumère les jetons ModuleRef qui représentent des modules importés.</span><span class="sxs-lookup"><span data-stu-id="c0567-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0567-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0567-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0567-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0567-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c0567-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c0567-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c0567-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c0567-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="c0567-108">à Tableau utilisé pour stocker les jetons ModuleRef.</span><span class="sxs-lookup"><span data-stu-id="c0567-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c0567-109">[in] Taille maximale du tableau `rModuleRefs`.</span><span class="sxs-lookup"><span data-stu-id="c0567-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="c0567-110">à Nombre de jetons ModuleRef retournés dans `rModuleRefs` .</span><span class="sxs-lookup"><span data-stu-id="c0567-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0567-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c0567-111">Return Value</span></span>  
  
|<span data-ttu-id="c0567-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0567-112">HRESULT</span></span>|<span data-ttu-id="c0567-113">Description</span><span class="sxs-lookup"><span data-stu-id="c0567-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c0567-114">`EnumModuleRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c0567-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c0567-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c0567-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c0567-116">Dans ce cas, `pcModuleRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="c0567-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0567-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0567-117">Requirements</span></span>  
 <span data-ttu-id="c0567-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0567-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0567-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c0567-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0567-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c0567-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0567-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0567-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0567-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0567-122">See also</span></span>

- [<span data-ttu-id="c0567-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c0567-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c0567-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c0567-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
