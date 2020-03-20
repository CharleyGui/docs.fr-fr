---
title: IMetaDataInfo::GetFileMapping, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataInfo.GetFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataInfo::GetFileMapping
helpviewer_keywords:
- IMetaDataInfo::GetFileMapping method [.NET Framework metadata]
- GetFileMapping method [.NET Framework metadata]
ms.assetid: 2868dfec-c992-4606-88bb-a8e0b6b18271
topic_type:
- apiref
ms.openlocfilehash: 0f5bdf97132c05e765cd6fa423a19bb996105d28
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175263"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="7424d-102">IMetaDataInfo::GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="7424d-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="7424d-103">Obtient la région de mémoire du fichier cartographié, et le type de cartographie.</span><span class="sxs-lookup"><span data-stu-id="7424d-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7424d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7424d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7424d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7424d-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="7424d-106">[out] Un pointeur pour le début du fichier cartographié.</span><span class="sxs-lookup"><span data-stu-id="7424d-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="7424d-107">[out] La taille de la région cartographiée.</span><span class="sxs-lookup"><span data-stu-id="7424d-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="7424d-108">Si `pdwMappingType` `fmFlat`c’est, c’est la taille du fichier.</span><span class="sxs-lookup"><span data-stu-id="7424d-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="7424d-109">[out] Une valeur [De CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) qui indique le type de cartographie.</span><span class="sxs-lookup"><span data-stu-id="7424d-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="7424d-110">La mise en œuvre actuelle de l’heure de course de langue commune (CLR) revient `fmFlat`toujours .</span><span class="sxs-lookup"><span data-stu-id="7424d-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="7424d-111">Les autres valeurs sont réservées pour un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="7424d-111">Other values are reserved for future use.</span></span> <span data-ttu-id="7424d-112">Toutefois, vous devez toujours vérifier la valeur retournée, car d’autres valeurs peuvent être activées dans les versions futures ou les versions de service.</span><span class="sxs-lookup"><span data-stu-id="7424d-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7424d-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7424d-113">Return Value</span></span>  
  
|<span data-ttu-id="7424d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7424d-114">HRESULT</span></span>|<span data-ttu-id="7424d-115">Description</span><span class="sxs-lookup"><span data-stu-id="7424d-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7424d-116">Toutes les sorties sont remplies.</span><span class="sxs-lookup"><span data-stu-id="7424d-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="7424d-117">NULL a été adopté comme une valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="7424d-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="7424d-118">La mise en œuvre du CLR ne peut pas fournir d’informations sur la région de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="7424d-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="7424d-119">Ceci peut se produire pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="7424d-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="7424d-120">- Le champ d’application `ofWrite` des `ofCopyMemory` métadonnées a été ouvert avec le ou le drapeau.</span><span class="sxs-lookup"><span data-stu-id="7424d-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="7424d-121">- La portée des métadonnées a été ouverte sans le `ofReadOnly` drapeau.</span><span class="sxs-lookup"><span data-stu-id="7424d-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="7424d-122">- La méthode [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) méthode a été utilisé pour ouvrir seulement la partie métadonnées du fichier.</span><span class="sxs-lookup"><span data-stu-id="7424d-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="7424d-123">- Le fichier n’est pas un fichier portable exécutable (PE).</span><span class="sxs-lookup"><span data-stu-id="7424d-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="7424d-124">**Note:**  Ces conditions dépendent de la mise en œuvre du CLR et risquent d’être affaiblies dans les versions futures du CLR.</span><span class="sxs-lookup"><span data-stu-id="7424d-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7424d-125">Notes </span><span class="sxs-lookup"><span data-stu-id="7424d-125">Remarks</span></span>  
 <span data-ttu-id="7424d-126">La mémoire `ppvData` qui pointe vers est valable seulement tant que la portée sous-jacente des métadonnées est ouverte.</span><span class="sxs-lookup"><span data-stu-id="7424d-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="7424d-127">Pour que cette méthode fonctionne, lorsque vous cartographiez les métadonnées d’un fichier sur disque en mémoire en appelant la `ofReadOnly` méthode [IMetaDataDispenser ::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) méthode, vous devez spécifier le drapeau et vous ne devez pas spécifier le ou `ofWrite` `ofCopyMemory` le drapeau.</span><span class="sxs-lookup"><span data-stu-id="7424d-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="7424d-128">Le choix du type de cartographie des fichiers pour chaque portée est spécifique à une mise en œuvre donnée du CLR.</span><span class="sxs-lookup"><span data-stu-id="7424d-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="7424d-129">Il ne peut pas être défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7424d-129">It cannot be set by the user.</span></span> <span data-ttu-id="7424d-130">La mise en œuvre `fmFlat` `pdwMappingType`actuelle du CLR revient toujours, mais cela peut changer dans les versions futures du CLR ou dans les versions de service futures d’une version donnée.</span><span class="sxs-lookup"><span data-stu-id="7424d-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="7424d-131">Vous devez toujours vérifier `pdwMappingType`la valeur retournée, parce que différents types auront des mises en page et des compensations différentes.</span><span class="sxs-lookup"><span data-stu-id="7424d-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="7424d-132">Le passage de NULL pour l’un ou l’autre des trois paramètres n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7424d-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="7424d-133">La méthode `E_INVALIDARG`revient, et aucune des sorties n’est remplie.</span><span class="sxs-lookup"><span data-stu-id="7424d-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="7424d-134">Ignorer le type de cartographie ou la taille de la région peut entraîner une interruption anormale du programme.</span><span class="sxs-lookup"><span data-stu-id="7424d-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7424d-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7424d-135">Requirements</span></span>  
 <span data-ttu-id="7424d-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7424d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7424d-137">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7424d-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7424d-138">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7424d-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7424d-139">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7424d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7424d-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7424d-140">See also</span></span>

- [<span data-ttu-id="7424d-141">IMetaDataInfo, interface</span><span class="sxs-lookup"><span data-stu-id="7424d-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="7424d-142">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="7424d-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
