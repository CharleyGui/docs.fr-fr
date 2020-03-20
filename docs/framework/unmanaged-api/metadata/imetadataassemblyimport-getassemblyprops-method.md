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
ms.openlocfilehash: dfa900e2184a8c415d75f5702c572b14c4018749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177789"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="b0153-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b0153-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="b0153-103">Obtient l’ensemble des propriétés pour l’assemblage avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b0153-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0153-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0153-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b0153-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b0153-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="b0153-106">[in].</span><span class="sxs-lookup"><span data-stu-id="b0153-106">[in].</span></span> <span data-ttu-id="b0153-107">Le `mdAssembly` jeton de métadonnées qui représente l’assemblage pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b0153-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="b0153-108">[out] Un pointeur à la clé publique ou le jeton des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b0153-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b0153-109">[out] Le nombre d’octets dans la clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="b0153-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="b0153-110">[out] Un pointeur à l’algorithme utilisé pour hachage les fichiers dans l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b0153-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="b0153-111">[out] Le nom simple de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="b0153-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b0153-112">[dans] La taille, en chars `szName`larges, de .</span><span class="sxs-lookup"><span data-stu-id="b0153-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="b0153-113">[out] Le nombre de chars `szName`larges effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="b0153-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="b0153-114">[out] Un pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b0153-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="b0153-115">[out] Drapeaux qui décrivent les métadonnées appliquées à un assemblage.</span><span class="sxs-lookup"><span data-stu-id="b0153-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="b0153-116">Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b0153-116">This value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0153-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b0153-117">Requirements</span></span>  
 <span data-ttu-id="b0153-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0153-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0153-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b0153-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0153-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b0153-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0153-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0153-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0153-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0153-122">See also</span></span>

- [<span data-ttu-id="b0153-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="b0153-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
