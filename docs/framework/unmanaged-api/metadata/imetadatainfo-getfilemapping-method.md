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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22af95ef4bd1fca0a8253faa6ce0e1c7a862054d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782662"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="aaa2c-102">IMetaDataInfo::GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="aaa2c-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="aaa2c-103">Obtient la zone de mémoire du fichier mappé et le type de mappage.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaa2c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aaa2c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,   
    [out] ULONGLONG            *pcbData,   
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aaa2c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aaa2c-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="aaa2c-106">[out] Pointeur vers le début du fichier mappé.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="aaa2c-107">[out] La taille de la région mappée.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="aaa2c-108">Si `pdwMappingType` est `fmFlat`, c’est la taille du fichier.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="aaa2c-109">[out] Un [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) valeur qui indique le type de mappage.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-109">[out] A [CorFileMapping](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="aaa2c-110">L’implémentation actuelle du common language runtime (CLR) retourne toujours `fmFlat`.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="aaa2c-111">Autres valeurs sont réservées pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-111">Other values are reserved for future use.</span></span> <span data-ttu-id="aaa2c-112">Toutefois, vous devez toujours vérifier la valeur retournée, étant donné que les autres valeurs peuvent être activées dans les versions ou versions de service.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aaa2c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aaa2c-113">Return Value</span></span>  
  
|<span data-ttu-id="aaa2c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aaa2c-114">HRESULT</span></span>|<span data-ttu-id="aaa2c-115">Description</span><span class="sxs-lookup"><span data-stu-id="aaa2c-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aaa2c-116">Toutes les sorties sont remplies.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="aaa2c-117">NULL a été transmise en tant que valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="aaa2c-118">L’implémentation CLR ne peut pas fournir d’informations sur la région de mémoire.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="aaa2c-119">Cela peut se produire pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="aaa2c-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="aaa2c-120">-La portée des métadonnées a été ouverte avec le `ofWrite` ou `ofCopyMemory` indicateur.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="aaa2c-121">-La portée des métadonnées a été ouverte sans le `ofReadOnly` indicateur.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="aaa2c-122">-Le [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) méthode a été utilisée pour ouvrir uniquement la partie métadonnées du fichier.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="aaa2c-123">-Le fichier n’est pas un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="aaa2c-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="aaa2c-124">**Remarque :**  Ces conditions dépendent de l’implémentation CLR et sont susceptibles d’être affaiblies dans les futures versions du CLR.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaa2c-125">Notes</span><span class="sxs-lookup"><span data-stu-id="aaa2c-125">Remarks</span></span>  
 <span data-ttu-id="aaa2c-126">La mémoire qui `ppvData` pointe est valide tant que la portée des métadonnées sous-jacentes est ouverte.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="aaa2c-127">Afin que cette méthode fonctionne, lorsque vous mappez les métadonnées d’un fichier sur disque dans la mémoire en appelant le [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) (méthode), vous devez spécifier le `ofReadOnly` indicateur et vous ne devez pas spécifier le `ofWrite` ou `ofCopyMemory` indicateur.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="aaa2c-128">Le choix du type de mappage de fichier pour chaque étendue est spécifique à une implémentation donnée du CLR.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="aaa2c-129">Elle ne peut pas être définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-129">It cannot be set by the user.</span></span> <span data-ttu-id="aaa2c-130">L’implémentation actuelle du CLR retourne toujours `fmFlat` dans `pdwMappingType`, mais cela peut changer dans les futures versions du CLR ou dans les versions de service d’une version donnée.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="aaa2c-131">Vous devez toujours vérifier la valeur retournée `pdwMappingType`, car différents types ont différentes dispositions et les décalages.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="aaa2c-132">Passage de NULL pour une des trois paramètres n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="aaa2c-133">La méthode retourne `E_INVALIDARG`, et aucune des sorties sont remplis.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="aaa2c-134">Ignorer le type de mappage ou la taille de la région peut entraîner l’arrêt du programme anormale.</span><span class="sxs-lookup"><span data-stu-id="aaa2c-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaa2c-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aaa2c-135">Requirements</span></span>  
 <span data-ttu-id="aaa2c-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaa2c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaa2c-137">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="aaa2c-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aaa2c-138">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aaa2c-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aaa2c-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaa2c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaa2c-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaa2c-140">See also</span></span>

- [<span data-ttu-id="aaa2c-141">IMetaDataInfo, interface</span><span class="sxs-lookup"><span data-stu-id="aaa2c-141">IMetaDataInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)
- [<span data-ttu-id="aaa2c-142">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="aaa2c-142">CorFileMapping Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corfilemapping-enumeration.md)
