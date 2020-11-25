---
title: IMetaDataEmit::SetModuleProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 1757662d2004dce3156182c35b37237ff91bae7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730339"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="e91a1-102">IMetaDataEmit::SetModuleProps, méthode</span><span class="sxs-lookup"><span data-stu-id="e91a1-102">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="e91a1-103">Met à jour les références à un module défini par un appel antérieur à [IMetaDataEmit ::D efinemoduleref](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="e91a1-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e91a1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e91a1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e91a1-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="e91a1-106">dans Nom du module en Unicode.</span><span class="sxs-lookup"><span data-stu-id="e91a1-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="e91a1-107">Il s’agit du nom de fichier uniquement, et non du nom de chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="e91a1-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91a1-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e91a1-108">Requirements</span></span>  

 <span data-ttu-id="e91a1-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e91a1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e91a1-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e91a1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e91a1-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e91a1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e91a1-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e91a1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91a1-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e91a1-113">See also</span></span>

- [<span data-ttu-id="e91a1-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e91a1-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e91a1-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e91a1-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
