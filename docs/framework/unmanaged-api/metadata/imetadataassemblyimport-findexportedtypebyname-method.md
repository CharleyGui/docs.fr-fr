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
ms.openlocfilehash: b1672d98d76241e5af4b6b60a38785f1278e15a8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731590"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="7a2fc-102">IMetaDataAssemblyImport::FindExportedTypeByName, méthode</span><span class="sxs-lookup"><span data-stu-id="7a2fc-102">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="7a2fc-103">Obtient un pointeur vers un type exporté, en fonction de son nom et du type englobant.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-103">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a2fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a2fc-104">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a2fc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7a2fc-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="7a2fc-106">dans Nom du type exporté.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-106">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="7a2fc-107">dans Jeton de métadonnées pour la classe englobante du type exporté.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-107">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="7a2fc-108">Cette valeur est `mdExportedTypeNil` si le type exporté demandé n’est pas un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-108">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="7a2fc-109">à Pointeur vers le `mdExportedType` jeton qui représente le type exporté.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-109">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a2fc-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="7a2fc-110">Remarks</span></span>  

 <span data-ttu-id="7a2fc-111">La `FindExportedTypeByName` méthode utilise les règles standard utilisées par le Common Language Runtime pour résoudre les références.</span><span class="sxs-lookup"><span data-stu-id="7a2fc-111">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a2fc-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7a2fc-112">Requirements</span></span>  

 <span data-ttu-id="7a2fc-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a2fc-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a2fc-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7a2fc-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a2fc-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7a2fc-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a2fc-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a2fc-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a2fc-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a2fc-117">See also</span></span>

- [<span data-ttu-id="7a2fc-118">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="7a2fc-118">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7a2fc-119">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="7a2fc-119">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
