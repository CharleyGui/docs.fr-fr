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
ms.openlocfilehash: 5ef5d9ae3da4dff13a461162f0ba3466d3d8192c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501259"
---
# <a name="imetadatainfogetfilemapping-method"></a><span data-ttu-id="b785e-102">IMetaDataInfo::GetFileMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="b785e-102">IMetaDataInfo::GetFileMapping Method</span></span>
<span data-ttu-id="b785e-103">Obtient la région de la mémoire du fichier mappé et le type de mappage.</span><span class="sxs-lookup"><span data-stu-id="b785e-103">Gets the memory region of the mapped file, and the type of mapping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b785e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b785e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileMapping (  
    [out] const void           **ppvData,
    [out] ULONGLONG            *pcbData,
    [out] DWORD                *pdwMappingType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b785e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b785e-105">Parameters</span></span>  
 `ppvData`  
 <span data-ttu-id="b785e-106">à Pointeur vers le début du fichier mappé.</span><span class="sxs-lookup"><span data-stu-id="b785e-106">[out] A pointer to the start of the mapped file.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b785e-107">à Taille de la région mappée.</span><span class="sxs-lookup"><span data-stu-id="b785e-107">[out] The size of the mapped region.</span></span> <span data-ttu-id="b785e-108">Si `pdwMappingType` a `fmFlat` la valeur, il s’agit de la taille du fichier.</span><span class="sxs-lookup"><span data-stu-id="b785e-108">If `pdwMappingType` is `fmFlat`, this is the size of the file.</span></span>  
  
 `pdwMappingType`  
 <span data-ttu-id="b785e-109">à Valeur [CorFileMapping,](corfilemapping-enumeration.md) qui indique le type de mappage.</span><span class="sxs-lookup"><span data-stu-id="b785e-109">[out] A [CorFileMapping](corfilemapping-enumeration.md) value that indicates the type of mapping.</span></span> <span data-ttu-id="b785e-110">L’implémentation actuelle du common language runtime (CLR) retourne toujours `fmFlat` .</span><span class="sxs-lookup"><span data-stu-id="b785e-110">The current implementation of the common language runtime (CLR) always returns `fmFlat`.</span></span> <span data-ttu-id="b785e-111">Les autres valeurs sont réservées pour un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="b785e-111">Other values are reserved for future use.</span></span> <span data-ttu-id="b785e-112">Toutefois, vous devez toujours vérifier la valeur renvoyée, car d’autres valeurs peuvent être activées dans les versions ultérieures ou les versions de service.</span><span class="sxs-lookup"><span data-stu-id="b785e-112">However, you should always verify the returned value, because other values may be enabled in future versions or service releases.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b785e-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="b785e-113">Return Value</span></span>  
  
|<span data-ttu-id="b785e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b785e-114">HRESULT</span></span>|<span data-ttu-id="b785e-115">Description</span><span class="sxs-lookup"><span data-stu-id="b785e-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b785e-116">Toutes les sorties sont remplies.</span><span class="sxs-lookup"><span data-stu-id="b785e-116">All outputs are filled.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b785e-117">La valeur NULL a été transmise en tant que valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="b785e-117">NULL was passed as an argument value.</span></span>|  
|`COR_E_NOTSUPPORTED`|<span data-ttu-id="b785e-118">L’implémentation du CLR ne peut pas fournir d’informations sur la région de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="b785e-118">The CLR implementation cannot provide information about the memory region.</span></span> <span data-ttu-id="b785e-119">Ceci peut se produire pour les raisons suivantes :</span><span class="sxs-lookup"><span data-stu-id="b785e-119">This can happen for the following reasons:</span></span><br /><br /> <span data-ttu-id="b785e-120">-La portée des métadonnées a été ouverte avec l' `ofWrite` `ofCopyMemory` indicateur ou.</span><span class="sxs-lookup"><span data-stu-id="b785e-120">-   The metadata scope was opened with the `ofWrite` or `ofCopyMemory` flag.</span></span><br /><span data-ttu-id="b785e-121">-La portée des métadonnées a été ouverte sans l' `ofReadOnly` indicateur.</span><span class="sxs-lookup"><span data-stu-id="b785e-121">-   The metadata scope was opened without the `ofReadOnly` flag.</span></span><br /><span data-ttu-id="b785e-122">-La méthode [IMetaDataDispenser :: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) a été utilisée pour ouvrir uniquement la partie métadonnées du fichier.</span><span class="sxs-lookup"><span data-stu-id="b785e-122">-   The [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method was used to open only the metadata portion of the file.</span></span><br /><span data-ttu-id="b785e-123">-Le fichier n’est pas un fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="b785e-123">-   The file is not a portable executable (PE) file.</span></span> <span data-ttu-id="b785e-124">**Remarque :**  Ces conditions dépendent de l’implémentation du CLR et sont susceptibles d’être assouplies dans les futures versions du CLR.</span><span class="sxs-lookup"><span data-stu-id="b785e-124">**Note:**  These conditions depend on the CLR implementation, and are likely to be weakened in future versions of the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b785e-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="b785e-125">Remarks</span></span>  
 <span data-ttu-id="b785e-126">La mémoire `ppvData` vers laquelle pointe est valide uniquement tant que la portée des métadonnées sous-jacentes est ouverte.</span><span class="sxs-lookup"><span data-stu-id="b785e-126">The memory that `ppvData` points to is valid only as long as the underlying metadata scope is open.</span></span>  
  
 <span data-ttu-id="b785e-127">Pour que cette méthode fonctionne, lorsque vous mappez les métadonnées d’un fichier sur disque en mémoire en appelant la méthode [IMetaDataDispenser :: OpenScope](imetadatadispenser-openscope-method.md) , vous devez spécifier l' `ofReadOnly` indicateur et vous ne devez pas spécifier l' `ofWrite` `ofCopyMemory` indicateur ou.</span><span class="sxs-lookup"><span data-stu-id="b785e-127">In order for this method to work, when you map the metadata of an on-disk file into memory by calling the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, you must specify the `ofReadOnly` flag and you must not specify the `ofWrite` or `ofCopyMemory` flag.</span></span>  
  
 <span data-ttu-id="b785e-128">Le choix du type de mappage de fichier pour chaque étendue est spécifique à une implémentation donnée du CLR.</span><span class="sxs-lookup"><span data-stu-id="b785e-128">The choice of file mapping type for each scope is specific to a given implementation of the CLR.</span></span> <span data-ttu-id="b785e-129">Il ne peut pas être défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b785e-129">It cannot be set by the user.</span></span> <span data-ttu-id="b785e-130">L’implémentation actuelle du CLR retourne toujours `fmFlat` dans `pdwMappingType` , mais cela peut changer dans les futures versions du CLR ou dans les futures versions de service d’une version donnée.</span><span class="sxs-lookup"><span data-stu-id="b785e-130">The current implementation of the CLR always returns `fmFlat` in `pdwMappingType`, but this can change in future versions of the CLR or in future service releases of a given version.</span></span> <span data-ttu-id="b785e-131">Vous devez toujours vérifier la valeur retournée dans `pdwMappingType` , car les différents types auront des dispositions et des décalages différents.</span><span class="sxs-lookup"><span data-stu-id="b785e-131">You should always check the returned value in `pdwMappingType`, because different types will have different layouts and offsets.</span></span>  
  
 <span data-ttu-id="b785e-132">La transmission de NULL pour l’un des trois paramètres n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="b785e-132">Passing NULL for any of the three parameters is not supported.</span></span> <span data-ttu-id="b785e-133">La méthode retourne `E_INVALIDARG` , et aucune des sorties n’est remplie.</span><span class="sxs-lookup"><span data-stu-id="b785e-133">The method returns `E_INVALIDARG`, and none of the outputs are filled.</span></span> <span data-ttu-id="b785e-134">Si vous ignorez le type de mappage ou la taille de la région, vous risquez de provoquer un arrêt anormal du programme.</span><span class="sxs-lookup"><span data-stu-id="b785e-134">Ignoring the mapping type or the size of the region can result in abnormal program termination.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b785e-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b785e-135">Requirements</span></span>  
 <span data-ttu-id="b785e-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b785e-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b785e-137">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b785e-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b785e-138">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b785e-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b785e-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b785e-139">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b785e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b785e-140">See also</span></span>

- [<span data-ttu-id="b785e-141">IMetaDataInfo, interface</span><span class="sxs-lookup"><span data-stu-id="b785e-141">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)
- [<span data-ttu-id="b785e-142">CorFileMapping, énumération</span><span class="sxs-lookup"><span data-stu-id="b785e-142">CorFileMapping Enumeration</span></span>](corfilemapping-enumeration.md)
