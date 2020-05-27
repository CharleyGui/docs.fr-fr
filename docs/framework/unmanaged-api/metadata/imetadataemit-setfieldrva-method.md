---
title: IMetaDataEmit::SetFieldRVA, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: d429995e41006798aee5f796150bedbd6ae87f6f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003866"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="c2c35-102">IMetaDataEmit::SetFieldRVA, méthode</span><span class="sxs-lookup"><span data-stu-id="c2c35-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="c2c35-103">Définit une valeur de variable globale pour l’adresse virtuelle relative du champ référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="c2c35-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2c35-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2c35-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2c35-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="c2c35-106">dans Jeton pour le champ cible.</span><span class="sxs-lookup"><span data-stu-id="c2c35-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c2c35-107">dans Adresse d’un code ou d’une zone de données.</span><span class="sxs-lookup"><span data-stu-id="c2c35-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c35-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c2c35-108">Requirements</span></span>  
 <span data-ttu-id="c2c35-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c35-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c35-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c2c35-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2c35-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c2c35-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2c35-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2c35-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c35-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2c35-113">See also</span></span>

- [<span data-ttu-id="c2c35-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c2c35-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c2c35-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="c2c35-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
