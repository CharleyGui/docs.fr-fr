---
title: IMetaDataAssemblyEmit::DefineAssembly, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssembly
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineAssembly method [.NET Framework metadata]
- DefineAssembly method [.NET Framework metadata]
ms.assetid: a0637d66-74bf-4f2d-8137-9ff838bccece
topic_type:
- apiref
ms.openlocfilehash: 14bd352099890e4ca36321d550b8e982d4373231
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177890"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="99d73-102">IMetaDataAssemblyEmit::DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="99d73-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="99d73-103">Crée `Assembly` une structure contenant des métadonnées pour l’assemblage spécifié et renvoie le jeton des métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="99d73-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99d73-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssembly (  
    [in]  void                 *pbPublicKey,  
    [in]  ULONG                cbPublicKey,  
    [in]  ULONG                uHashAlgId,  
    [in]  LPCWSTR              szName,
    [in]  ASSEMBLYMETADATA     *pMetaData,  
    [in]  DWORD                dwAssemblyFlags,  
    [out] mdAssembly           *pmda  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99d73-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="99d73-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="99d73-106">[dans] La clé publique qui identifie l’éditeur de l’assemblée, ou NULL si l’assemblée n’est pas fortement nommée.</span><span class="sxs-lookup"><span data-stu-id="99d73-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="99d73-107">[dans] La taille dans `pbPublicKey`les octets de .</span><span class="sxs-lookup"><span data-stu-id="99d73-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="99d73-108">[dans] L’identifiant de l’algorithme de hachage à utiliser pour chiffrer les fichiers dans l’assemblage, ou NULL pour spécifier l’algorithme SHA-1.</span><span class="sxs-lookup"><span data-stu-id="99d73-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="99d73-109">[dans] Le nom de texte lisible par l’homme de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="99d73-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="99d73-110">Cette valeur ne doit pas dépasser 1024 caractères.</span><span class="sxs-lookup"><span data-stu-id="99d73-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="99d73-111">[dans] Un pointeur à une instance ASSEMBLYMETADATA qui contient la version, la plate-forme et les informations locales pour l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="99d73-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="99d73-112">[dans] Une combinaison de valeurs [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) qui décrivent les caractéristiques de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="99d73-112">[in] A combination of [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="99d73-113">[out] Un pointeur vers le jeton des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="99d73-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99d73-114">Notes </span><span class="sxs-lookup"><span data-stu-id="99d73-114">Remarks</span></span>  
 <span data-ttu-id="99d73-115">Une `Assembly` seule structure de métadonnées peut être définie dans un manifeste.</span><span class="sxs-lookup"><span data-stu-id="99d73-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d73-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="99d73-116">Requirements</span></span>  
 <span data-ttu-id="99d73-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99d73-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99d73-118">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="99d73-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99d73-119">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99d73-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99d73-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99d73-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d73-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99d73-121">See also</span></span>

- [<span data-ttu-id="99d73-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="99d73-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
