---
title: IMetaDataEmit::DefinePermissionSet, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: a069e2f4ec5d4114e9504fa5a58c5066fdfd7249
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008038"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="29fc6-102">IMetaDataEmit::DefinePermissionSet, méthode</span><span class="sxs-lookup"><span data-stu-id="29fc6-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="29fc6-103">Crée une définition pour un jeu d’autorisations avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="29fc6-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29fc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29fc6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29fc6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29fc6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="29fc6-106">dans Objet à décoréer.</span><span class="sxs-lookup"><span data-stu-id="29fc6-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="29fc6-107">dans Valeur [CorDeclSecurity,](cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="29fc6-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="29fc6-108">dans Objet BLOB d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="29fc6-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="29fc6-109">dans Taille, en octets, de `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="29fc6-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="29fc6-110">à Jeton d’autorisation retourné.</span><span class="sxs-lookup"><span data-stu-id="29fc6-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29fc6-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="29fc6-111">Requirements</span></span>  
 <span data-ttu-id="29fc6-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29fc6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29fc6-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="29fc6-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29fc6-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="29fc6-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29fc6-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29fc6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29fc6-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29fc6-116">See also</span></span>

- [<span data-ttu-id="29fc6-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="29fc6-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="29fc6-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="29fc6-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
