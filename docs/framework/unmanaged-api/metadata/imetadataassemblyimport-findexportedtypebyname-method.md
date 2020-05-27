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
ms.openlocfilehash: ac6de9a16fad6ba9d14f3960ddd28c42c111f254
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009390"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="6eb66-102">IMetaDataAssemblyImport::FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="6eb66-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>
<span data-ttu-id="6eb66-103">Obtient un pointeur vers un type exporté, en fonction de son nom et du type englobant.</span><span class="sxs-lookup"><span data-stu-id="6eb66-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb66-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eb66-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6eb66-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6eb66-106">dans Nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="6eb66-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="6eb66-107">dans Jeton de métadonnées pour la classe englobante du type exporté.</span><span class="sxs-lookup"><span data-stu-id="6eb66-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="6eb66-108">Cette valeur est `mdExportedTypeNil` si le type exporté demandé n’est pas un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="6eb66-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="6eb66-109">à Pointeur vers le `mdExportedType` jeton qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="6eb66-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb66-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="6eb66-110">Remarks</span></span>  
 <span data-ttu-id="6eb66-111">La `FindExportedTypeByName` méthode utilise les règles standard utilisées par le Common Language Runtime pour résoudre les références.</span><span class="sxs-lookup"><span data-stu-id="6eb66-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eb66-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6eb66-112">Requirements</span></span>  
 <span data-ttu-id="6eb66-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6eb66-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6eb66-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6eb66-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6eb66-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6eb66-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6eb66-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6eb66-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb66-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6eb66-117">See also</span></span>

- [<span data-ttu-id="6eb66-118">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="6eb66-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="6eb66-119">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="6eb66-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
