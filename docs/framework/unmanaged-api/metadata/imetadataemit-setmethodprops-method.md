---
title: IMetaDataEmit::SetMethodProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: c461582cc22f7185ee2707db91be83bc1aa0ba4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706834"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="12eda-102">IMetaDataEmit::SetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="12eda-102">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="12eda-103">Définit ou met à jour la fonctionnalité, stockée à l’adresse virtuelle relative spécifiée, d’une méthode définie par un appel antérieur à [IMetaDataEmit ::D efinemethod](imetadataemit-definemethod-method.md).</span><span class="sxs-lookup"><span data-stu-id="12eda-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12eda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12eda-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12eda-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12eda-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="12eda-106">dans Jeton de la méthode à modifier.</span><span class="sxs-lookup"><span data-stu-id="12eda-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="12eda-107">dans Attributs du membre.</span><span class="sxs-lookup"><span data-stu-id="12eda-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="12eda-108">dans Adresse du code.</span><span class="sxs-lookup"><span data-stu-id="12eda-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="12eda-109">dans Indicateurs d’implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="12eda-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12eda-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="12eda-110">Requirements</span></span>  

 <span data-ttu-id="12eda-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12eda-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12eda-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="12eda-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12eda-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12eda-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12eda-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12eda-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12eda-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12eda-115">See also</span></span>

- [<span data-ttu-id="12eda-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="12eda-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="12eda-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="12eda-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
