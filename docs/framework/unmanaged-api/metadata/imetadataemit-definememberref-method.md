---
title: IMetaDataEmit::DefineMemberRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004689"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="e4e3a-102">IMetaDataEmit::DefineMemberRef, méthode</span><span class="sxs-lookup"><span data-stu-id="e4e3a-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="e4e3a-103">Définit une référence à un membre d’un module à l’extérieur de la portée actuelle et obtient un jeton pour cette définition de référence.</span><span class="sxs-lookup"><span data-stu-id="e4e3a-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4e3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4e3a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4e3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4e3a-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="e4e3a-106">dans Jeton pour la classe ou l’interface du membre cible, si le membre n’est pas global ; Si le membre est global, `mdModuleRef` jeton pour cet autre fichier.</span><span class="sxs-lookup"><span data-stu-id="e4e3a-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="e4e3a-107">dans Nom du membre cible.</span><span class="sxs-lookup"><span data-stu-id="e4e3a-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e4e3a-108">dans Signature du membre cible.</span><span class="sxs-lookup"><span data-stu-id="e4e3a-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e4e3a-109">dans Nombre d’octets dans `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="e4e3a-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="e4e3a-110">à `mdMemberRef`Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="e4e3a-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e3a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e4e3a-111">Requirements</span></span>  
 <span data-ttu-id="e4e3a-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4e3a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e3a-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e4e3a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4e3a-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4e3a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4e3a-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e3a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e3a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4e3a-116">See also</span></span>

- [<span data-ttu-id="e4e3a-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e4e3a-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e4e3a-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e4e3a-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
