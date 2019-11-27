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
ms.openlocfilehash: 0b7ca6f9878ed2fa2d90ea93e5101f0a66ec2d5e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440207"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="e8c36-102">IMetaDataAssemblyEmit::DefineFile, méthode</span><span class="sxs-lookup"><span data-stu-id="e8c36-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="e8c36-103">Crée une structure `File` contenant les métadonnées pour l'assembly référencé par cet assembly et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="e8c36-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8c36-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8c36-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8c36-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="e8c36-106">dans Nom du fichier à consommer.</span><span class="sxs-lookup"><span data-stu-id="e8c36-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="e8c36-107">dans Pointeur vers les données de hachage associées à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e8c36-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="e8c36-108">dans Taille en octets de `pbHashValue`.</span><span class="sxs-lookup"><span data-stu-id="e8c36-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="e8c36-109">dans Combinaison d’opérations de bits de `FileFlags` valeurs qui spécifient des paramètres de propriété.</span><span class="sxs-lookup"><span data-stu-id="e8c36-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="e8c36-110">à Pointeur vers le jeton de `File` retourné.</span><span class="sxs-lookup"><span data-stu-id="e8c36-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8c36-111">Notes</span><span class="sxs-lookup"><span data-stu-id="e8c36-111">Remarks</span></span>  
 <span data-ttu-id="e8c36-112">Une `File` structure de métadonnées doit être définie pour chaque fichier qui faisait partie de cet assembly au moment de la génération de cet assembly, à l’exception du fichier qui contient les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="e8c36-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c36-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e8c36-113">Requirements</span></span>  
 <span data-ttu-id="e8c36-114">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c36-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c36-115">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e8c36-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8c36-116">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e8c36-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8c36-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c36-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c36-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8c36-118">See also</span></span>

- [<span data-ttu-id="e8c36-119">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e8c36-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
