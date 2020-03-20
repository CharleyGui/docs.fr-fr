---
title: IMetaDataAssemblyEmit::DefineFile, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
ms.openlocfilehash: cabd6a47e5d6fc2a4cea87b16d349d9c778b3507
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176056"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="392f5-102">IMetaDataAssemblyEmit::DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="392f5-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="392f5-103">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="392f5-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="392f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="392f5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,
    [in]  const void     *pbHashValue,
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="392f5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="392f5-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="392f5-106">[dans] Le nom du fichier à consommer.</span><span class="sxs-lookup"><span data-stu-id="392f5-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="392f5-107">[dans] Un pointeur vers les données de hachage associées à l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="392f5-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="392f5-108">[dans] La taille dans `pbHashValue`les octets de .</span><span class="sxs-lookup"><span data-stu-id="392f5-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="392f5-109">[dans] Une combinaison de `FileFlags` valeurs qui spécifient les paramètres de propriété.</span><span class="sxs-lookup"><span data-stu-id="392f5-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="392f5-110">[out] Un pointeur `File` au jeton retourné.</span><span class="sxs-lookup"><span data-stu-id="392f5-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="392f5-111">Notes </span><span class="sxs-lookup"><span data-stu-id="392f5-111">Remarks</span></span>  
 <span data-ttu-id="392f5-112">Une `File` structure de métadonnées doit être définie pour chaque fichier qui faisait partie de cet assemblage au moment de la construction de cet assemblage, à l’exclusion du fichier qui contient les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="392f5-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="392f5-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="392f5-113">Requirements</span></span>  
 <span data-ttu-id="392f5-114">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="392f5-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="392f5-115">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="392f5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="392f5-116">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="392f5-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="392f5-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="392f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="392f5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="392f5-118">See also</span></span>

- [<span data-ttu-id="392f5-119">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="392f5-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
