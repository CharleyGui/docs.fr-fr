---
title: IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyRefProps
helpviewer_keywords:
- SetAssemblyRefProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 70a32bf3-9051-4f96-ae87-11356d06a073
topic_type:
- apiref
ms.openlocfilehash: fb381a872cbeb787da0c6920f2cdeef434fb33ea
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008090"
---
# <a name="imetadataassemblyemitsetassemblyrefprops-method"></a><span data-ttu-id="04e2a-102">IMetaDataAssemblyEmit::SetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="04e2a-102">IMetaDataAssemblyEmit::SetAssemblyRefProps Method</span></span>
<span data-ttu-id="04e2a-103">Modifie la structure de métadonnées `AssemblyRef` spécifiée.</span><span class="sxs-lookup"><span data-stu-id="04e2a-103">Modifies the specified `AssemblyRef` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e2a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyRefProps (  
    [in] mdAssemblyRef              ar,  
    [in] const void                 *pbPublicKeyOrToken,  
    [in] ULONG                      cbPublicKeyOrToken,  
    [in] LPCWSTR                    szName,
    [in] const ASSEMBLYMETADATA     *pMetaData,
    [in] const void                 *pbHashValue,  
    [in] ULONG                      cbHashValue,  
    [in] DWORD                      dwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e2a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04e2a-105">Parameters</span></span>  
 `ar`  
 <span data-ttu-id="04e2a-106">dans Jeton de métadonnées qui spécifie la `AssemblyRef` structure de métadonnées à modifier.</span><span class="sxs-lookup"><span data-stu-id="04e2a-106">[in] The metadata token that specifies the `AssemblyRef` metadata structure to be modified.</span></span>  
  
 `pbPublicKeyOrToken`  
 <span data-ttu-id="04e2a-107">dans Clé publique de l’éditeur de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="04e2a-107">[in] The public key of the publisher of the referenced assembly.</span></span>  
  
 `cbPublicKeyOrToken`  
 <span data-ttu-id="04e2a-108">dans Taille en octets de `pbPublicKeyOrToken` .</span><span class="sxs-lookup"><span data-stu-id="04e2a-108">[in] The size in bytes of `pbPublicKeyOrToken`.</span></span>  
  
 `szName`  
 <span data-ttu-id="04e2a-109">dans Nom de texte explicite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04e2a-109">[in] The human-readable text name of the assembly.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="04e2a-110">dans Pointeur vers une instance ASSEMBLYMETADATA qui contient les informations relatives à la version, à la plateforme et aux paramètres régionaux de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04e2a-110">[in] A pointer to an ASSEMBLYMETADATA instance that contains the version, platform, and locale information for the assembly.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="04e2a-111">dans Pointeur vers les données de hachage associées à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="04e2a-111">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="04e2a-112">dans Taille en octets de `pbHashValue` .</span><span class="sxs-lookup"><span data-stu-id="04e2a-112">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwAssemblyRefFlags`  
 <span data-ttu-id="04e2a-113">dans Combinaison d’opérations de bits de valeurs [AssemblyRefFlags,](assemblyrefflags-enumeration.md) qui spécifient des attributs de l’assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="04e2a-113">[in] A bitwise combination of [AssemblyRefFlags](assemblyrefflags-enumeration.md) values that specify attributes of the referenced assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04e2a-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="04e2a-114">Remarks</span></span>  
 <span data-ttu-id="04e2a-115">Pour créer une `AssemblyRef` structure de métadonnées, utilisez la méthode [IMetaDataAssemblyEmit ::D efineassemblyref](imetadataassemblyemit-defineassemblyref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="04e2a-115">To create an `AssemblyRef` metadata structure, use the [IMetaDataAssemblyEmit::DefineAssemblyRef](imetadataassemblyemit-defineassemblyref-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e2a-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04e2a-116">Requirements</span></span>  
 <span data-ttu-id="04e2a-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e2a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e2a-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04e2a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e2a-119">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04e2a-119">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e2a-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e2a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e2a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04e2a-121">See also</span></span>

- [<span data-ttu-id="04e2a-122">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="04e2a-122">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
