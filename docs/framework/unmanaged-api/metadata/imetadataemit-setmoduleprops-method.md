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
ms.openlocfilehash: aee258c49e6726ebef990257456fd273b01b9ef0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007843"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="055a0-102">IMetaDataEmit::SetModuleProps, méthode</span><span class="sxs-lookup"><span data-stu-id="055a0-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="055a0-103">Met à jour les références à un module défini par un appel antérieur à [IMetaDataEmit ::D efinemoduleref](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="055a0-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="055a0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="055a0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="055a0-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="055a0-106">dans Nom du module en Unicode.</span><span class="sxs-lookup"><span data-stu-id="055a0-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="055a0-107">Il s’agit du nom de fichier uniquement, et non du nom de chemin d’accès complet.</span><span class="sxs-lookup"><span data-stu-id="055a0-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055a0-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="055a0-108">Requirements</span></span>  
 <span data-ttu-id="055a0-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="055a0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="055a0-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="055a0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="055a0-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="055a0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="055a0-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="055a0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055a0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="055a0-113">See also</span></span>

- [<span data-ttu-id="055a0-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="055a0-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="055a0-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="055a0-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
