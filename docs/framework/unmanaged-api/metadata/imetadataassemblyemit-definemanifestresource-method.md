---
title: IMetaDataAssemblyEmit::DefineManifestResource, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineManifestResource
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineManifestResource
helpviewer_keywords:
- DefineManifestResource method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineManifestResource method [.NET Framework metadata]
ms.assetid: 27f6d295-0fe9-4cda-b77e-6e7d5c53df09
topic_type:
- apiref
ms.openlocfilehash: 83170815f4aa65988bb6a6394bd466a0ba376ebf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432054"
---
# <a name="imetadataassemblyemitdefinemanifestresource-method"></a><span data-ttu-id="dd31a-102">IMetaDataAssemblyEmit::DefineManifestResource, méthode</span><span class="sxs-lookup"><span data-stu-id="dd31a-102">IMetaDataAssemblyEmit::DefineManifestResource Method</span></span>
<span data-ttu-id="dd31a-103">Crée une structure `ManifestResource` contenant les métadonnées pour la ressource de manifeste spécifiée et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="dd31a-103">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd31a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd31a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineManifestResource (  
    [in] LPCWSTR                szName,   
    [in] mdToken                tkImplementation,   
    [in] DWORD                  dwOffset,   
    [in] DWORD                  dwResourceFlags,  
    [out] mdManifestResource    *pmdmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd31a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd31a-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="dd31a-106">dans Nom de la ressource.</span><span class="sxs-lookup"><span data-stu-id="dd31a-106">[in] The name of the resource.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="dd31a-107">dans Un jeton de métadonnées de type `mdtFile` ou `mdtAssemblyRef` qui est mappé au fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="dd31a-107">[in] A metadata token of type `mdtFile` or `mdtAssemblyRef` that maps to the resource provider.</span></span> <span data-ttu-id="dd31a-108">Une valeur NULL indique que le fichier dans lequel les métadonnées sont incorporées est le fournisseur de ressources.</span><span class="sxs-lookup"><span data-stu-id="dd31a-108">A NULL value indicates that the file in which the metadata is embedded is the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="dd31a-109">dans Offset au début de la ressource dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="dd31a-109">[in] The offset to the beginning of the resource within the file.</span></span> <span data-ttu-id="dd31a-110">Pour les ressources de fichiers autonomes, cette valeur est toujours égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="dd31a-110">For resources in standalone files, this will always be zero.</span></span> <span data-ttu-id="dd31a-111">Si la ressource est incorporée dans un fichier PE (exécutable portable), il s’agit d’un décalage de l’objet BLOB de ressources, qui démarre à l’emplacement spécifié dans le fichier d’en-tête Cor. h.</span><span class="sxs-lookup"><span data-stu-id="dd31a-111">If the resource is embedded in a PE (portable executable) file, this is an offset of the resource BLOB, which starts at the location specified in the cor.h header file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="dd31a-112">dans Combinaison d’opérations de bits de valeurs d’indicateur qui spécifient des paramètres de propriété pour la définition de ressource.</span><span class="sxs-lookup"><span data-stu-id="dd31a-112">[in] A bitwise combination of flag values that specify property settings for the resource definition.</span></span>  
  
 `pmdmr`  
 <span data-ttu-id="dd31a-113">à Pointeur vers le jeton de métadonnées retourné.</span><span class="sxs-lookup"><span data-stu-id="dd31a-113">[out] A pointer to the returned metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd31a-114">Notes</span><span class="sxs-lookup"><span data-stu-id="dd31a-114">Remarks</span></span>  
 <span data-ttu-id="dd31a-115">Une `ManifestResource` structure de métadonnées doit être définie pour chaque ressource implémentée dans chacun des fichiers de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="dd31a-115">One `ManifestResource` metadata structure must be defined for each resource that is implemented in each of the assembly's files.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd31a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dd31a-116">Requirements</span></span>  
 <span data-ttu-id="dd31a-117">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd31a-117">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd31a-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd31a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd31a-119">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd31a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd31a-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd31a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd31a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd31a-121">See also</span></span>

- [<span data-ttu-id="dd31a-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="dd31a-122">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
