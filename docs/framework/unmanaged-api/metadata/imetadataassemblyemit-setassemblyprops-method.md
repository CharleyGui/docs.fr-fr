---
title: IMetaDataAssemblyEmit::SetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34335321207e98a518ff3e0fdb5ea1dc3ac68b75
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776263"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a><span data-ttu-id="a2dac-102">IMetaDataAssemblyEmit::SetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="a2dac-102">IMetaDataAssemblyEmit::SetAssemblyProps Method</span></span>
<span data-ttu-id="a2dac-103">Modifie la structure de métadonnées `Assembly` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a2dac-103">Modifies the specified `Assembly` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2dac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2dac-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2dac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2dac-105">Parameters</span></span>  
 `pma`  
 <span data-ttu-id="a2dac-106">[in] Le jeton de métadonnées qui spécifie le `Assembly` structure des métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="a2dac-106">[in] The metadata token that specifies the `Assembly` metadata structure to be modified.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="a2dac-107">[in] Pointeur vers la clé publique du serveur de publication de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2dac-107">[in] A pointer to the public key of the publisher of the assembly.</span></span>  
  
 `cbPublicKey`  
 <span data-ttu-id="a2dac-108">[in] La taille en octets de `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="a2dac-108">[in] The size in bytes of `pbPublicKey`.</span></span>  
  
 `ulHashAlgId`  
 <span data-ttu-id="a2dac-109">[in] L’identificateur pour l’algorithme de hachage utilisé pour hacher les fichiers d’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2dac-109">[in] The identifier for the hash algorithm used to hash the assembly files.</span></span>  
  
 `szName`  
 <span data-ttu-id="a2dac-110">[in] Le nom lisible de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2dac-110">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="a2dac-111">[in] Pointeur vers le ASSEMBLYMETADATA qui contient des informations de version, la plateforme et aux paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2dac-111">[in] A pointer to the ASSEMBLYMETADATA that contains version, platform, and locale information for the assembly.</span></span>  
  
 `dwAssemblyFlags`  
 <span data-ttu-id="a2dac-112">[in] Une combinaison au niveau du bit de [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) valeurs qui spécifient différents attributs de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2dac-112">[in] A bitwise combination of [AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md) values that specify various attributes of the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2dac-113">Notes</span><span class="sxs-lookup"><span data-stu-id="a2dac-113">Remarks</span></span>  
 <span data-ttu-id="a2dac-114">Pour créer un `Assembly` structure des métadonnées, utilisez le [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="a2dac-114">To create an `Assembly` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssembly](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2dac-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2dac-115">Requirements</span></span>  
 <span data-ttu-id="a2dac-116">**Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2dac-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2dac-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a2dac-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2dac-118">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2dac-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2dac-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2dac-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2dac-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2dac-120">See also</span></span>

- [<span data-ttu-id="a2dac-121">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a2dac-121">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
