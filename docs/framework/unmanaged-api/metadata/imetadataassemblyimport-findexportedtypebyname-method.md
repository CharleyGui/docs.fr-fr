---
title: IMetaDataAssemblyImport::FindExportedTypeByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: edfe5de9c9d7ef9607a2eea5146194bbd4393a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175991"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="a9bf1-102">IMetaDataAssemblyImport::FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="a9bf1-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="a9bf1-103">Obtient un pointeur vers un type exporté, donné son nom et le type d’enclos.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bf1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9bf1-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9bf1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9bf1-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="a9bf1-106">[dans] Le nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="a9bf1-107">[dans] Les métadonnées symboliques pour la classe d’enceinte du type exporté.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="a9bf1-108">Cette valeur `mdExportedTypeNil` est si le type exporté demandé n’est pas un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="a9bf1-109">[out] Un pointeur `mdExportedType` vers le jeton qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9bf1-110">Notes </span><span class="sxs-lookup"><span data-stu-id="a9bf1-110">Remarks</span></span>  
 <span data-ttu-id="a9bf1-111">La `FindExportedTypeByName` méthode utilise les règles standard employées par l’heure d’exécution de langue commune pour résoudre des références.</span><span class="sxs-lookup"><span data-stu-id="a9bf1-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bf1-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9bf1-112">Requirements</span></span>  
 <span data-ttu-id="a9bf1-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9bf1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bf1-114">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="a9bf1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9bf1-115">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9bf1-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9bf1-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bf1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bf1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9bf1-117">See also</span></span>

- [<span data-ttu-id="a9bf1-118">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="a9bf1-118">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="a9bf1-119">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="a9bf1-119">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
