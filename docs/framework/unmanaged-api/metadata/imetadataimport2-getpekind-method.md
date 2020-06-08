---
title: IMetaDataImport2::GetPEKind, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490430"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="dd498-102">IMetaDataImport2::GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="dd498-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="dd498-103">Obtient une valeur identifiant la nature du code dans le fichier exécutable portable (PE), en général un fichier DLL ou EXE, qui est défini dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="dd498-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd498-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd498-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd498-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dd498-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="dd498-106">à Pointeur vers une valeur de l’énumération [CorPEKind,](corpekind-enumeration.md) qui décrit le fichier PE.</span><span class="sxs-lookup"><span data-stu-id="dd498-106">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="dd498-107">à Pointeur vers une valeur qui identifie l’architecture de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd498-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="dd498-108">Consultez la section suivante pour connaître les valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="dd498-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd498-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="dd498-109">Remarks</span></span>  
 <span data-ttu-id="dd498-110">La valeur référencée par le `pdwMachine` paramètre peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="dd498-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="dd498-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="dd498-111">Value</span></span>|<span data-ttu-id="dd498-112">Architecture de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="dd498-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="dd498-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="dd498-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="dd498-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="dd498-114">0x014C</span></span>|<span data-ttu-id="dd498-115">x86</span><span class="sxs-lookup"><span data-stu-id="dd498-115">x86</span></span>|  
|<span data-ttu-id="dd498-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="dd498-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="dd498-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="dd498-117">0x0200</span></span>|<span data-ttu-id="dd498-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="dd498-118">Intel IPF</span></span>|  
|<span data-ttu-id="dd498-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="dd498-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="dd498-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="dd498-120">0x8664</span></span>|<span data-ttu-id="dd498-121">x64</span><span class="sxs-lookup"><span data-stu-id="dd498-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd498-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="dd498-122">Requirements</span></span>  
 <span data-ttu-id="dd498-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd498-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd498-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dd498-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dd498-125">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd498-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dd498-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd498-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd498-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd498-127">See also</span></span>

- [<span data-ttu-id="dd498-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="dd498-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="dd498-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="dd498-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="dd498-130">CorPEKind, énumération</span><span class="sxs-lookup"><span data-stu-id="dd498-130">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
