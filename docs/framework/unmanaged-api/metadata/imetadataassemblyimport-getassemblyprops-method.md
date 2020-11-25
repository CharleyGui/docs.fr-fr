---
title: IMetaDataAssemblyImport::GetAssemblyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733891"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="34b96-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="34b96-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>

<span data-ttu-id="34b96-103">Obtient le jeu de propriétés de l’assembly avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="34b96-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34b96-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34b96-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34b96-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="34b96-105">Parameters</span></span>  

 `mda`  
 <span data-ttu-id="34b96-106">[in].</span><span class="sxs-lookup"><span data-stu-id="34b96-106">[in].</span></span> <span data-ttu-id="34b96-107">`mdAssembly`Jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="34b96-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="34b96-108">à Pointeur vers la clé publique ou le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="34b96-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="34b96-109">à Nombre d’octets dans la clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="34b96-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="34b96-110">à Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="34b96-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="34b96-111">à Nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="34b96-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="34b96-112">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="34b96-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="34b96-113">à Nombre de caractères larges réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="34b96-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="34b96-114">à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="34b96-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="34b96-115">à Indicateurs qui décrivent les métadonnées appliquées à un assembly.</span><span class="sxs-lookup"><span data-stu-id="34b96-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="34b96-116">Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="34b96-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34b96-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="34b96-117">Requirements</span></span>  

 <span data-ttu-id="34b96-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34b96-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34b96-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="34b96-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="34b96-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="34b96-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="34b96-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34b96-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b96-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34b96-122">See also</span></span>

- [<span data-ttu-id="34b96-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="34b96-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
