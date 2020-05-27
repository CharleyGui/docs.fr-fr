---
title: IMetaDataEmit::SetPermissionSetProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007804"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="80e03-102">IMetaDataEmit::SetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="80e03-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="80e03-103">Définit ou met à jour les fonctionnalités de la signature de métadonnées d’un jeu d’autorisations défini par un appel antérieur à [IMetaDataEmit ::D efinepermissionset](imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="80e03-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80e03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80e03-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80e03-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80e03-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="80e03-106">dans Jeton de métadonnées qui représente l’objet à décoréer.</span><span class="sxs-lookup"><span data-stu-id="80e03-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="80e03-107">dans Valeur [CorDeclSecurity,](cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="80e03-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="80e03-108">dans Objet BLOB d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="80e03-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="80e03-109">dans Taille, en octets, de `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="80e03-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="80e03-110">à Un `mdPermission` jeton de métadonnées qui représente les autorisations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="80e03-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80e03-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="80e03-111">Requirements</span></span>  
 <span data-ttu-id="80e03-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80e03-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80e03-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="80e03-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80e03-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="80e03-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80e03-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80e03-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e03-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80e03-116">See also</span></span>

- [<span data-ttu-id="80e03-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="80e03-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="80e03-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="80e03-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
