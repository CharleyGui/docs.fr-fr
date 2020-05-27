---
title: IMetaDataAssemblyEmit::DefineAssemblyRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineAssemblyRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineAssemblyRef
helpviewer_keywords:
- DefineAssemblyRef method [.NET Framework metadata]
- IMetaDataAssemblyEmit::DefineAssemblyRef method [.NET Framework metadata]
ms.assetid: 0b284b18-0084-4b3a-912a-5ebe9f29c88b
topic_type:
- apiref
ms.openlocfilehash: 612463bca18c23fac0b086adde2d208a0fbc5ae5
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008168"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="dcda8-102">IMetaDataAssemblyEmit::DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="dcda8-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>
<span data-ttu-id="dcda8-103">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="dcda8-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcda8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcda8-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineAssemblyRef (  
    [in]  void                *pbPublicKeyOrToken,  
    [in]  ULONG               cbPublicKeyOrToken,  
    [in]  LPCWSTR             szName,  
    [in]  ASSEMBLYMETADATA    pMetaData,  
    [in]  void                *pbHashValue,  
    [in]  ULONG               cbHashValue,  
    [in]  DWORD               dwAssemblyRefFlags,  
    [out] mdAssemblyRef       *pmdar  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcda8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dcda8-105">Parameters</span></span>  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="dcda8-106">dans Clé publique de l’éditeur de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dcda8-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="dcda8-107">La fonction d’assistance [StrongNameTokenFromAssembly (](../strong-naming/strongnametokenfromassembly-function.md) peut être utilisée pour obtenir le hachage de la clé publique à passer comme ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="dcda8-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="dcda8-108">dans Taille en octets de `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="dcda8-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="dcda8-109">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="dcda8-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="dcda8-110">Cette valeur ne doit pas dépasser 1024 caractères.</span><span class="sxs-lookup"><span data-stu-id="dcda8-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="dcda8-111">dans Instance ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dcda8-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="dcda8-112">dans Données de hachage associées à l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="dcda8-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="dcda8-113">facultatif.</span><span class="sxs-lookup"><span data-stu-id="dcda8-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="dcda8-114">dans Taille en octets de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="dcda8-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="dcda8-115">dans Combinaison d’opérations de bits de valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) qui influencent le comportement du moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dcda8-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="dcda8-116">à Pointeur vers le jeton de `AssemblyRef` métadonnées retourné.</span><span class="sxs-lookup"><span data-stu-id="dcda8-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcda8-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="dcda8-117">Remarks</span></span>  
 <span data-ttu-id="dcda8-118">Une `AssemblyRef` structure de métadonnées doit être définie pour chaque assembly référencé par cet assembly.</span><span class="sxs-lookup"><span data-stu-id="dcda8-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="dcda8-119">Au moment de l’exécution, les détails d’un assembly référencé sont passés au programme de résolution d’assembly et indiquent qu’ils représentent les informations « comme étant générées ».</span><span class="sxs-lookup"><span data-stu-id="dcda8-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="dcda8-120">Le programme de résolution d’assembly applique ensuite la stratégie.</span><span class="sxs-lookup"><span data-stu-id="dcda8-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcda8-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dcda8-121">Requirements</span></span>  
 <span data-ttu-id="dcda8-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcda8-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcda8-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dcda8-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dcda8-124">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dcda8-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dcda8-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcda8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcda8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcda8-126">See also</span></span>

- [<span data-ttu-id="dcda8-127">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="dcda8-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
