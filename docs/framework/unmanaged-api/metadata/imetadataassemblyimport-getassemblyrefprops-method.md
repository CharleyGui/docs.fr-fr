---
title: IMetaDataAssemblyImport::GetAssemblyRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 4149db74adfa26df221eed5c590766a023bb105e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448227"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="deccb-102">IMetaDataAssemblyImport::GetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="deccb-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="deccb-103">Obtient le jeu de propriétés pour la référence d’assembly avec la signature de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="deccb-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="deccb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="deccb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="deccb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="deccb-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="deccb-106">dans `mdAssemblyRef` jeton de métadonnées qui représente la référence d’assembly pour laquelle obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="deccb-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="deccb-107">à Pointeur vers la clé publique ou le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="deccb-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="deccb-108">à Nombre d’octets dans la clé publique ou le jeton retourné.</span><span class="sxs-lookup"><span data-stu-id="deccb-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="deccb-109">à Nom simple de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="deccb-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="deccb-110">dans Taille, en caractères larges, de `szName`.</span><span class="sxs-lookup"><span data-stu-id="deccb-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="deccb-111">à Pointeur vers le nombre de caractères larges réellement retournés dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="deccb-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="deccb-112">à Pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="deccb-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="deccb-113">à Pointeur vers la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="deccb-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="deccb-114">Il s’agit du hachage, à l’aide de l’algorithme SHA-1, de la propriété `PublicKey` de l’assembly référencé, sauf si l’indicateur arfFullOriginator de l’énumération [AssemblyRefFlags,](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) est défini.</span><span class="sxs-lookup"><span data-stu-id="deccb-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="deccb-115">à Nombre de caractères larges dans la valeur de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="deccb-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="deccb-116">à Pointeur vers des indicateurs qui décrivent les métadonnées appliquées à un assembly.</span><span class="sxs-lookup"><span data-stu-id="deccb-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="deccb-117">La valeur flags est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags,](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="deccb-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="deccb-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="deccb-118">Return Value</span></span>  
 <span data-ttu-id="deccb-119">Cette méthode retourne S_OK si elle est réussie ; Sinon, elle retourne l’un des codes d’erreur définis dans le fichier d’en-tête winerror. h.</span><span class="sxs-lookup"><span data-stu-id="deccb-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="deccb-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="deccb-120">Requirements</span></span>  
 <span data-ttu-id="deccb-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deccb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="deccb-122">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="deccb-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="deccb-123">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="deccb-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="deccb-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="deccb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="deccb-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="deccb-125">See also</span></span>

- [<span data-ttu-id="deccb-126">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="deccb-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
