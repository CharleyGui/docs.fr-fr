---
title: IMetaDataEmit::DefineModuleRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
ms.openlocfilehash: efff491d92ac7910f43f76965ef98d1d0e4ba0aa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004424"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="f674e-102">IMetaDataEmit::DefineModuleRef, méthode</span><span class="sxs-lookup"><span data-stu-id="f674e-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="f674e-103">Crée la signature de métadonnées pour un module avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="f674e-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f674e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f674e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineModuleRef (
    [in]  LPCWSTR           szName,
    [out] mdModuleRef       *pmur
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f674e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f674e-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="f674e-106">dans Nom des autres fichiers de métadonnées, en général une DLL.</span><span class="sxs-lookup"><span data-stu-id="f674e-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="f674e-107">Il s’agit du nom de fichier uniquement.</span><span class="sxs-lookup"><span data-stu-id="f674e-107">This is the file name only.</span></span> <span data-ttu-id="f674e-108">N’utilisez pas un nom de chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="f674e-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="f674e-109">à Jeton assigné `mdModuleRef` .</span><span class="sxs-lookup"><span data-stu-id="f674e-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f674e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f674e-110">Requirements</span></span>  
 <span data-ttu-id="f674e-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f674e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f674e-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f674e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f674e-113">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f674e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f674e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f674e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f674e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f674e-115">See also</span></span>

- [<span data-ttu-id="f674e-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f674e-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f674e-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f674e-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
