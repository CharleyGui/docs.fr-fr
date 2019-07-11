---
title: IMetaDataAssemblyImport::GetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec04588bd1cc21e585d89c734c152a86fb835b15
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772721"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="61b49-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="61b49-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="61b49-103">Obtient le jeu de propriétés pour l’assembly avec la signature de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="61b49-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61b49-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61b49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,   
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61b49-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61b49-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="61b49-106">[in].</span><span class="sxs-lookup"><span data-stu-id="61b49-106">[in].</span></span> <span data-ttu-id="61b49-107">Le `mdAssembly` jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="61b49-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="61b49-108">[out] Pointeur vers la clé publique ou le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="61b49-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="61b49-109">[out] Le nombre d’octets dans la clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="61b49-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="61b49-110">[out] Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="61b49-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="61b49-111">[out] Le nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="61b49-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="61b49-112">[in] La taille, en caractères étendus de `szName`.</span><span class="sxs-lookup"><span data-stu-id="61b49-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="61b49-113">[out] Le nombre de caractères étendus réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="61b49-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="61b49-114">[out] Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="61b49-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="61b49-115">[out] Indicateurs qui décrivent les métadonnées appliquées à un assembly.</span><span class="sxs-lookup"><span data-stu-id="61b49-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="61b49-116">Cette valeur est une combinaison d’une ou plusieurs [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) valeurs.</span><span class="sxs-lookup"><span data-stu-id="61b49-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b49-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61b49-117">Requirements</span></span>  
 <span data-ttu-id="61b49-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b49-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b49-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61b49-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61b49-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61b49-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61b49-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b49-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b49-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61b49-122">See also</span></span>

- [<span data-ttu-id="61b49-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="61b49-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
