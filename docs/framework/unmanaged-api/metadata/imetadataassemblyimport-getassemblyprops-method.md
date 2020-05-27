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
ms.openlocfilehash: a90deaf3e9ddf326c6fca558cbb4681fc40e022d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009052"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="54402-102">IMetaDataAssemblyImport::GetAssemblyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="54402-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>
<span data-ttu-id="54402-103">Obtient le jeu de propriétés de l’assembly avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="54402-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54402-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54402-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="54402-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54402-105">Parameters</span></span>  
 `mda`  
 <span data-ttu-id="54402-106">[in].</span><span class="sxs-lookup"><span data-stu-id="54402-106">[in].</span></span> <span data-ttu-id="54402-107">`mdAssembly`Jeton de métadonnées qui représente l’assembly pour lequel obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="54402-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="54402-108">à Pointeur vers la clé publique ou le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="54402-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="54402-109">à Nombre d’octets dans la clé publique retournée.</span><span class="sxs-lookup"><span data-stu-id="54402-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="54402-110">à Pointeur vers l’algorithme utilisé pour hacher les fichiers dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="54402-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="54402-111">à Nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="54402-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="54402-112">dans Taille, en caractères larges, de `szName` .</span><span class="sxs-lookup"><span data-stu-id="54402-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="54402-113">à Nombre de caractères larges réellement retournés dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="54402-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="54402-114">à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="54402-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="54402-115">à Indicateurs qui décrivent les métadonnées appliquées à un assembly.</span><span class="sxs-lookup"><span data-stu-id="54402-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="54402-116">Cette valeur est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="54402-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54402-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="54402-117">Requirements</span></span>  
 <span data-ttu-id="54402-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54402-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54402-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54402-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54402-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54402-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54402-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54402-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54402-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54402-122">See also</span></span>

- [<span data-ttu-id="54402-123">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="54402-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
