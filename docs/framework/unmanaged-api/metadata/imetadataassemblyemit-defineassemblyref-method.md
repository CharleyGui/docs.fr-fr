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
ms.openlocfilehash: ba53ff30f0b6d0ae7fed7db422b7c0a242204a2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689429"
---
# <a name="imetadataassemblyemitdefineassemblyref-method"></a><span data-ttu-id="7f77c-102">IMetaDataAssemblyEmit::DefineAssemblyRef, méthode</span><span class="sxs-lookup"><span data-stu-id="7f77c-102">IMetaDataAssemblyEmit::DefineAssemblyRef Method</span></span>

<span data-ttu-id="7f77c-103">Crée une structure `AssemblyRef` contenant les métadonnées pour l'assembly que cet assembly référence et retourne le jeton de métadonnées associé.</span><span class="sxs-lookup"><span data-stu-id="7f77c-103">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f77c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f77c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f77c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7f77c-105">Parameters</span></span>  

 `pbPublicKeyOrToken`  
 <span data-ttu-id="7f77c-106">dans Clé publique de l’éditeur de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7f77c-106">[in] The public key of the publisher of the referenced assembly.</span></span> <span data-ttu-id="7f77c-107">La fonction d’assistance [StrongNameTokenFromAssembly (](../strong-naming/strongnametokenfromassembly-function.md) peut être utilisée pour obtenir le hachage de la clé publique à passer comme ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="7f77c-107">The helper function [StrongNameTokenFromAssembly](../strong-naming/strongnametokenfromassembly-function.md) can be used to get the hash of the public key to pass as this parameter.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="7f77c-108">dans Taille en octets de `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="7f77c-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f77c-109">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7f77c-109">[in] The human-readable text name of the assembly.</span></span> <span data-ttu-id="7f77c-110">Cette valeur ne doit pas dépasser 1024 caractères.</span><span class="sxs-lookup"><span data-stu-id="7f77c-110">This value must not exceed 1024 characters.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="7f77c-111">dans Instance ASSEMBLYMETADATA qui contient les informations de version, de plateforme et de paramètres régionaux de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7f77c-111">[in] An ASSEMBLYMETADATA instance that contains the version, platform and locale information of the referenced assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="7f77c-112">dans Données de hachage associées à l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7f77c-112">[in] The hash data associated with the referenced assembly.</span></span> <span data-ttu-id="7f77c-113">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="7f77c-113">Optional.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="7f77c-114">dans Taille en octets de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="7f77c-114">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="7f77c-115">dans Combinaison d’opérations de bits de valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) qui influencent le comportement du moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7f77c-115">[in] A bitwise combination of [CorAssemblyFlags](corassemblyflags-enumeration.md) values that influence the behavior of the execution engine.</span></span>  
  
 `pmdar`  
 <span data-ttu-id="7f77c-116">à Pointeur vers le jeton de `AssemblyRef` métadonnées retourné.</span><span class="sxs-lookup"><span data-stu-id="7f77c-116">[out] A pointer to the returned `AssemblyRef` metadata token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f77c-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="7f77c-117">Remarks</span></span>  

 <span data-ttu-id="7f77c-118">Une `AssemblyRef` structure de métadonnées doit être définie pour chaque assembly référencé par cet assembly.</span><span class="sxs-lookup"><span data-stu-id="7f77c-118">One `AssemblyRef` metadata structure must be defined for each assembly that this assembly references.</span></span>  
  
 <span data-ttu-id="7f77c-119">Au moment de l’exécution, les détails d’un assembly référencé sont passés au programme de résolution d’assembly et indiquent qu’ils représentent les informations « comme étant générées ».</span><span class="sxs-lookup"><span data-stu-id="7f77c-119">At run time, the details of a referenced assembly are passed to the assembly resolver with an indication that they represent the "as built" information.</span></span> <span data-ttu-id="7f77c-120">Le programme de résolution d’assembly applique ensuite la stratégie.</span><span class="sxs-lookup"><span data-stu-id="7f77c-120">The assembly resolver then applies policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f77c-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7f77c-121">Requirements</span></span>  

 <span data-ttu-id="7f77c-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f77c-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f77c-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7f77c-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f77c-124">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f77c-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f77c-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f77c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f77c-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f77c-126">See also</span></span>

- [<span data-ttu-id="7f77c-127">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7f77c-127">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
