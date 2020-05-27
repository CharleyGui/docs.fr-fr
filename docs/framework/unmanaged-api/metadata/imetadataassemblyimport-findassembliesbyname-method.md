---
title: IMetaDataAssemblyImport::FindAssembliesByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindAssembliesByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindAssembliesByName
helpviewer_keywords:
- FindAssembliesByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindAssembliesByName method [.NET Framework metadata]
ms.assetid: 4db97cf9-e4c1-4233-8efa-cbdc0e14a8e4
topic_type:
- apiref
ms.openlocfilehash: 05902436c09d082f90af01f48c7e918650317ce7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009416"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="8cf6d-102">IMetaDataAssemblyImport::FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="8cf6d-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="8cf6d-103">Obtient un tableau d’assemblys avec le `szAssemblyName` paramètre spécifié, à l’aide des règles standard utilisées par le Common Language Runtime (CLR) pour la résolution des références.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cf6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cf6d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembliesByName (  
    [in]  LPCWSTR     szAppBase,
    [in]  LPCWSTR     szPrivateBin,
    [in]  LPCWSTR     szAssemblyName,
    [out] IUnknown    *ppIUnk[],
    [in]  ULONG       cMax,
    [out] ULONG       *pcAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cf6d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8cf6d-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="8cf6d-106">dans Répertoire racine dans lequel Rechercher l’assembly donné.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="8cf6d-107">Si cette valeur est définie sur `null` , `FindAssembliesByName` se présente uniquement dans le global assembly cache de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="8cf6d-108">dans Liste des sous-répertoires délimités par des points-virgules (par exemple, « bin ; BIN2 »), sous le répertoire racine dans lequel Rechercher l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="8cf6d-109">Ces répertoires sont détectés en plus de ceux spécifiés dans les règles de détection par défaut.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="8cf6d-110">dans Nom de l’assembly à rechercher.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="8cf6d-111">Le format de cette chaîne est défini dans la page de référence de la classe pour <xref:System.Reflection.AssemblyName> .</span><span class="sxs-lookup"><span data-stu-id="8cf6d-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="8cf6d-112">dans Tableau de type [IUnknown](/cpp/atl/iunknown) dans lequel placer les `IMetadataAssemblyImport` pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8cf6d-113">à Nombre maximal de pointeurs d’interface qui peuvent être placés dans `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="8cf6d-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="8cf6d-114">à Nombre de pointeurs d’interface retournés.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="8cf6d-115">Autrement dit, le nombre de pointeurs d’interface réellement placés dans `ppIUnk` .</span><span class="sxs-lookup"><span data-stu-id="8cf6d-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cf6d-116">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8cf6d-116">Return Value</span></span>  
  
|<span data-ttu-id="8cf6d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8cf6d-117">HRESULT</span></span>|<span data-ttu-id="8cf6d-118">Description</span><span class="sxs-lookup"><span data-stu-id="8cf6d-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8cf6d-119">`FindAssembliesByName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8cf6d-120">Il n’y a aucun assembly.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cf6d-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="8cf6d-121">Remarks</span></span>  
 <span data-ttu-id="8cf6d-122">Étant donné un nom d’assembly, la `FindAssembliesByName` méthode recherche l’assembly en suivant les règles standard pour la résolution des références d’assembly.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="8cf6d-123">(Pour plus d’informations, consultez [Comment le runtime localise les assemblys](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName`permet à l’appelant de configurer différents aspects du contexte du programme de résolution d’assembly, tels que la base de l’application et le chemin de recherche privé.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-123">(For more information, see [How the Runtime Locates Assemblies](../../deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="8cf6d-124">La `FindAssembliesByName` méthode requiert l’initialisation du CLR dans le processus afin d’appeler la logique de résolution d’assembly.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="8cf6d-125">Par conséquent, vous devez appeler [CoInitializeEE,](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (en passant COINITEE_DEFAULT) avant d’appeler `FindAssembliesByName` , puis suivre un appel à [CoUninitializeCor,](../hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="8cf6d-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="8cf6d-126">`FindAssembliesByName`retourne un pointeur [IMetaDataImport](imetadataimport-interface.md) vers le fichier contenant le manifeste d’assembly pour le nom de l’assembly qui est passé.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-126">`FindAssembliesByName` returns an [IMetaDataImport](imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="8cf6d-127">Si le nom de l’assembly donné n’est pas complètement spécifié (par exemple, s’il n’inclut pas de version), plusieurs assemblys peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="8cf6d-128">`FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assembly référencé au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="8cf6d-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cf6d-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8cf6d-129">Requirements</span></span>  
 <span data-ttu-id="8cf6d-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cf6d-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cf6d-131">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8cf6d-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8cf6d-132">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8cf6d-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8cf6d-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cf6d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf6d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cf6d-134">See also</span></span>

- [<span data-ttu-id="8cf6d-135">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="8cf6d-135">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="8cf6d-136">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="8cf6d-136">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
