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
ms.openlocfilehash: 3698525c139ed52b59ca577c598e675b6c26eef4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719513"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="f7fa3-102">IMetaDataEmit::DefinePermissionSet, méthode</span><span class="sxs-lookup"><span data-stu-id="f7fa3-102">IMetaDataEmit::DefinePermissionSet Method</span></span>

<span data-ttu-id="f7fa3-103">Crée une définition pour un jeu d’autorisations avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="f7fa3-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fa3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7fa3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7fa3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7fa3-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="f7fa3-106">dans Objet à décoréer.</span><span class="sxs-lookup"><span data-stu-id="f7fa3-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="f7fa3-107">dans Valeur [CorDeclSecurity,](cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f7fa3-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="f7fa3-108">dans Objet BLOB d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="f7fa3-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="f7fa3-109">dans Taille, en octets, de `pvPermission` .</span><span class="sxs-lookup"><span data-stu-id="f7fa3-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="f7fa3-110">à Jeton d’autorisation retourné.</span><span class="sxs-lookup"><span data-stu-id="f7fa3-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7fa3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7fa3-111">Requirements</span></span>  

 <span data-ttu-id="f7fa3-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7fa3-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7fa3-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7fa3-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7fa3-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7fa3-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7fa3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fa3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7fa3-116">See also</span></span>

- [<span data-ttu-id="f7fa3-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f7fa3-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f7fa3-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f7fa3-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
