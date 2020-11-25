---
title: IMetaDataEmit::SetMethodImplFlags, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: 486d545413337f6696bd9f21c516466fc3747256
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730355"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="c0274-102">IMetaDataEmit::SetMethodImplFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="c0274-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>

<span data-ttu-id="c0274-103">Définit ou met à jour la signature de métadonnées de l’implémentation de méthode héritée qui est référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="c0274-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0274-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0274-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (
    [in]  mdMethodDef   md,
    [in]  DWORD         dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0274-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0274-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="c0274-106">dans Jeton de la méthode à modifier.</span><span class="sxs-lookup"><span data-stu-id="c0274-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="c0274-107">dans Combinaison des valeurs de l’énumération [CorMethodImpl,](cormethodimpl-enumeration.md) qui spécifie les fonctionnalités d’implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c0274-107">[in] A combination of the values of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0274-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0274-108">Requirements</span></span>  

 <span data-ttu-id="c0274-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0274-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0274-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c0274-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0274-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0274-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0274-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0274-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0274-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0274-113">See also</span></span>

- [<span data-ttu-id="c0274-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c0274-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c0274-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="c0274-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
