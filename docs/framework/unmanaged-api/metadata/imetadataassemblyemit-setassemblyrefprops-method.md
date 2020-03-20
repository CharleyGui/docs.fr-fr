---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: 6ad6bbb8a4c69f575bbeba3a297c46e049a97325
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176043"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="c7682-102">IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="c7682-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="c7682-103">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c7682-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7682-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7682-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7682-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7682-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="c7682-106">[dans] Le jeton des métadonnées `AssemblyRef` qui spécifie la structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="c7682-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="c7682-107">[dans] La clé publique de l’éditeur de l’assemblée référencée.</span><span class="sxs-lookup"><span data-stu-id="c7682-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="c7682-108">[dans] La taille dans `pbPublicKeyOrToken`les octets de .</span><span class="sxs-lookup"><span data-stu-id="c7682-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="c7682-109">[dans] Le nom de texte lisible par l’homme de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="c7682-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="c7682-110">[dans] Un pointeur à une instance ASSEMBLYMETADATA qui contient la version, la plate-forme et les informations locales pour l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="c7682-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c7682-111">[dans] Un pointeur vers les données de hachage associées à l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="c7682-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c7682-112">[dans] La taille dans `pbHashValue`les octets de .</span><span class="sxs-lookup"><span data-stu-id="c7682-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="c7682-113">[dans] Une combinaison peu sage des valeurs [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) qui spécifient les attributs de l’assemblage référencé.</span><span class="sxs-lookup"><span data-stu-id="c7682-113">[in] A bitwise combination of [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7682-114">Notes </span><span class="sxs-lookup"><span data-stu-id="c7682-114">Remarks</span></span>  
 <span data-ttu-id="c7682-115">Pour créer `AssemblyRef` une structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit::DefineAssemblyRef.](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)</span><span class="sxs-lookup"><span data-stu-id="c7682-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7682-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7682-116">Requirements</span></span>  
 <span data-ttu-id="c7682-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7682-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7682-118">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="c7682-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c7682-119">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7682-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7682-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7682-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7682-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7682-121">See also</span></span>

- [<span data-ttu-id="c7682-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c7682-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
