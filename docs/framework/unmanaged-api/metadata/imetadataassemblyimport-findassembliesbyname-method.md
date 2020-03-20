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
ms.openlocfilehash: c0f81e3767d4ea3bc336203fbe8c914b4e2bd07b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177802"
---
# <a name="imetadataassemblyimportfindassembliesbyname-method"></a><span data-ttu-id="b4e69-102">IMetaDataAssemblyImport::FindAssembliesByName, méthode</span><span class="sxs-lookup"><span data-stu-id="b4e69-102">IMetaDataAssemblyImport::FindAssembliesByName Method</span></span>
<span data-ttu-id="b4e69-103">Obtient un éventail d’assemblages avec le paramètre spécifié, `szAssemblyName` en utilisant les règles standard employées par l’heure de circulation de langue commune (CLR) pour résoudre des références.</span><span class="sxs-lookup"><span data-stu-id="b4e69-103">Gets an array of assemblies with the specified `szAssemblyName` parameter, using the standard rules employed by the common language runtime (CLR) for resolving references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4e69-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b4e69-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b4e69-105">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="b4e69-106">[dans] Le répertoire racine dans lequel rechercher l’assemblage donné.</span><span class="sxs-lookup"><span data-stu-id="b4e69-106">[in] The root directory in which to search for the given assembly.</span></span> <span data-ttu-id="b4e69-107">Si cette valeur `null`est `FindAssembliesByName` définie à , ne regardera que dans le cache d’assemblage global pour l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b4e69-107">If this value is set to `null`, `FindAssembliesByName` will look only in the global assembly cache for the assembly.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="b4e69-108">[dans] Une liste de sous-directions semi-colons (par exemple, "bin;bin2"), sous le répertoire des racines, dans laquelle rechercher l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b4e69-108">[in] A list of semicolon-delimited subdirectories (for example, "bin;bin2"), under the root directory, in which to search for the assembly.</span></span> <span data-ttu-id="b4e69-109">Ces répertoires sont sondés en plus de ceux spécifiés dans les règles de sondage par défaut.</span><span class="sxs-lookup"><span data-stu-id="b4e69-109">These directories are probed in addition to those specified in the default probing rules.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="b4e69-110">[dans] Le nom de l’assemblée à trouver.</span><span class="sxs-lookup"><span data-stu-id="b4e69-110">[in] The name of the assembly to find.</span></span> <span data-ttu-id="b4e69-111">Le format de cette chaîne est défini <xref:System.Reflection.AssemblyName>dans la page de référence de la classe pour .</span><span class="sxs-lookup"><span data-stu-id="b4e69-111">The format of this string is defined in the class reference page for <xref:System.Reflection.AssemblyName>.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b4e69-112">[dans] Un tableau de type [IUnknown](/cpp/atl/iunknown) `IMetadataAssemblyImport` dans lequel mettre les pointeurs d’interface.</span><span class="sxs-lookup"><span data-stu-id="b4e69-112">[in] An array of type [IUnknown](/cpp/atl/iunknown) in which to put the `IMetadataAssemblyImport` interface pointers.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b4e69-113">[out] Le nombre maximum de pointeurs d’interface qui peuvent être placés en `ppIUnk`.</span><span class="sxs-lookup"><span data-stu-id="b4e69-113">[out] The maximum number of interface pointers that can be placed in `ppIUnk`.</span></span>  
  
 `pcAssemblies`  
 <span data-ttu-id="b4e69-114">[out] Le nombre de pointeurs d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="b4e69-114">[out] The number of interface pointers returned.</span></span> <span data-ttu-id="b4e69-115">C’est-à-dire, le nombre `ppIUnk`de pointeurs d’interface effectivement placés dans .</span><span class="sxs-lookup"><span data-stu-id="b4e69-115">That is, the number of interface pointers actually placed in `ppIUnk`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4e69-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b4e69-116">Return Value</span></span>  
  
|<span data-ttu-id="b4e69-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4e69-117">HRESULT</span></span>|<span data-ttu-id="b4e69-118">Description</span><span class="sxs-lookup"><span data-stu-id="b4e69-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b4e69-119">`FindAssembliesByName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b4e69-119">`FindAssembliesByName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b4e69-120">Il n’y a pas d’assemblées.</span><span class="sxs-lookup"><span data-stu-id="b4e69-120">There are no assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4e69-121">Notes </span><span class="sxs-lookup"><span data-stu-id="b4e69-121">Remarks</span></span>  
 <span data-ttu-id="b4e69-122">Compte tenu d’un nom d’assemblage, la `FindAssembliesByName` méthode trouve l’assemblage en suivant les règles standard pour résoudre les références d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b4e69-122">Given an assembly name, the `FindAssembliesByName` method finds the assembly by following the standard rules for resolving assembly references.</span></span> <span data-ttu-id="b4e69-123">(Pour plus d’informations, voir [Comment les assemblages De localisation de durée de course](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` permet à l’appelant de configurer divers aspects du contexte du résolveur d’assemblage, tels que la base d’application et le chemin de recherche privé.</span><span class="sxs-lookup"><span data-stu-id="b4e69-123">(For more information, see [How the Runtime Locates Assemblies](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).) `FindAssembliesByName` allows the caller to configure various aspects of the assembly resolver context, such as application base and private search path.</span></span>  
  
 <span data-ttu-id="b4e69-124">La `FindAssembliesByName` méthode exige que le CLR soit paradé dans le processus afin d’invoquer la logique de résolution de l’assemblage.</span><span class="sxs-lookup"><span data-stu-id="b4e69-124">The `FindAssembliesByName` method requires the CLR to be initialized in the process in order to invoke the assembly resolution logic.</span></span> <span data-ttu-id="b4e69-125">Par conséquent, vous devez appeler [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passant `FindAssembliesByName`COINITEE_DEFAULT) avant d’appeler , puis suivre avec un appel à [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span><span class="sxs-lookup"><span data-stu-id="b4e69-125">Therefore, you must call [CoInitializeEE](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) (passing COINITEE_DEFAULT) before calling `FindAssembliesByName`, and then follow with a call to [CoUninitializeCor](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md).</span></span>  
  
 <span data-ttu-id="b4e69-126">`FindAssembliesByName`renvoie un pointeur [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) au fichier contenant le manifeste d’assemblage pour le nom d’assemblage qui est transmis.</span><span class="sxs-lookup"><span data-stu-id="b4e69-126">`FindAssembliesByName` returns an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pointer to the file containing the assembly manifest for the assembly name that is passed in.</span></span> <span data-ttu-id="b4e69-127">Si le nom d’assemblage donné n’est pas entièrement spécifié (par exemple, s’il n’inclut pas de version), plusieurs assemblages peuvent être retournés.</span><span class="sxs-lookup"><span data-stu-id="b4e69-127">If the given assembly name is not fully specified (for example, if it does not include a version), multiple assemblies might be returned.</span></span>  
  
 <span data-ttu-id="b4e69-128">`FindAssembliesByName`est couramment utilisé par un compilateur qui tente de trouver un assemblage référencé au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b4e69-128">`FindAssembliesByName` is commonly used by a compiler that attempts to find a referenced assembly at compile time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4e69-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b4e69-129">Requirements</span></span>  
 <span data-ttu-id="b4e69-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4e69-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4e69-131">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b4e69-131">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b4e69-132">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b4e69-132">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b4e69-133">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4e69-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e69-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4e69-134">See also</span></span>

- [<span data-ttu-id="b4e69-135">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="b4e69-135">How the Runtime Locates Assemblies</span></span>](../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b4e69-136">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="b4e69-136">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
