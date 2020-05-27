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
ms.openlocfilehash: 17c91200730431c4c6e230b8c1561ce7c4863868
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008181"
---
# <a name="imetadataassemblyemitdefineassembly-method"></a><span data-ttu-id="85e39-102">IMetaDataAssemblyEmit::DefineAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="85e39-102">IMetaDataAssemblyEmit::DefineAssembly Method</span></span>
<span data-ttu-id="85e39-103">Crée une `Assembly` structure contenant les métadonnées pour l’assembly spécifié et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="85e39-103">Creates an `Assembly` structure containing metadata for the specified assembly and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85e39-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="85e39-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="85e39-105">Parameters</span></span>  
 `pbPublicKey`  
 <span data-ttu-id="85e39-106">dans Clé publique qui identifie le serveur de publication de l’assembly, ou NULL si l’assembly n’a pas un nom fort.</span><span class="sxs-lookup"><span data-stu-id="85e39-106">[in] The public key that identifies the publisher of the assembly, or NULL if the assembly is not strongly named.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="85e39-107">dans Taille en octets de `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="85e39-107">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="85e39-108">dans Identificateur de l’algorithme de hachage à utiliser pour chiffrer les fichiers de l’assembly, ou NULL pour spécifier l’algorithme SHA-1.</span><span class="sxs-lookup"><span data-stu-id="85e39-108">[in] The identifier of the hashing algorithm to use to encrypt the files in the assembly, or NULL to specify the SHA-1 algorithm.</span></span>  
  
 `szName`  
 <span data-ttu-id="85e39-109">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="85e39-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="85e39-110">Cette valeur ne doit pas dépasser 1024 caractères.</span><span class="sxs-lookup"><span data-stu-id="85e39-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="85e39-111">dans Pointeur vers une instance ASSEMBLYMETADATA qui contient les informations relatives à la version, à la plateforme et aux paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="85e39-111">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="85e39-112">dans Combinaison de valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) qui décrivent les fonctionnalités de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="85e39-112">[in] A combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that describe features of the assembly.</span></span>  
  
 `pmda`  
 <span data-ttu-id="85e39-113">à Pointeur vers le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="85e39-113">[out] A pointer to the metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e39-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="85e39-114">Remarks</span></span>  
 <span data-ttu-id="85e39-115">Une seule `Assembly` structure de métadonnées peut être définie dans un manifeste.</span><span class="sxs-lookup"><span data-stu-id="85e39-115">Only one `Assembly` metadata structure can be defined within a manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e39-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="85e39-116">Requirements</span></span>  
 <span data-ttu-id="85e39-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e39-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e39-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="85e39-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85e39-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="85e39-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85e39-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e39-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e39-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85e39-121">See also</span></span>

- [<span data-ttu-id="85e39-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="85e39-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
