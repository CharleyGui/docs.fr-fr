---
title: IMetaDataAssemblyImport::GetAssemblyFromScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
ms.openlocfilehash: dc40b4a7cf61f8d6141b8e3e57c5e13fe2261b35
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731564"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="9ca57-102">IMetaDataAssemblyImport::GetAssemblyFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="9ca57-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>

<span data-ttu-id="9ca57-103">Obtient un pointeur vers l’assembly dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="9ca57-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ca57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ca57-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ca57-105">Parameters</span></span>  

 `ptkAssembly`  
 <span data-ttu-id="9ca57-106">à Pointeur vers le jeton récupéré `mdAssembly` qui identifie l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9ca57-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca57-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ca57-107">Requirements</span></span>  

 <span data-ttu-id="9ca57-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca57-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca57-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9ca57-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ca57-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ca57-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ca57-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca57-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca57-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ca57-112">See also</span></span>

- [<span data-ttu-id="9ca57-113">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="9ca57-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
