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
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175965"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="1c876-102">IMetaDataAssemblyImport::GetAssemblyRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="1c876-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="1c876-103">Obtient l’ensemble des propriétés pour la référence d’assemblage avec la signature spécifiée de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="1c876-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c876-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c876-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1c876-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c876-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="1c876-106">[dans] Le `mdAssemblyRef` jeton de métadonnées qui représente la référence d’assemblage pour laquelle obtenir les propriétés.</span><span class="sxs-lookup"><span data-stu-id="1c876-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="1c876-107">[out] Un pointeur à la clé publique ou le jeton des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="1c876-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="1c876-108">[out] Le nombre d’octets dans la clé ou le jeton public retourné.</span><span class="sxs-lookup"><span data-stu-id="1c876-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="1c876-109">[out] Le nom simple de l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="1c876-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1c876-110">[dans] La taille, en chars `szName`larges, de .</span><span class="sxs-lookup"><span data-stu-id="1c876-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1c876-111">[out] Un pointeur sur le nombre de `szName`chars larges effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="1c876-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1c876-112">[out] Un pointeur vers une structure ASSEMBLYMETADATA qui contient les métadonnées d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="1c876-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="1c876-113">[out] Un pointeur à la valeur de hachage.</span><span class="sxs-lookup"><span data-stu-id="1c876-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="1c876-114">C’est le hachage, en utilisant l’algorithme SHA-1, de la `PublicKey` propriété de l’assemblage en cours de référence, à moins que le drapeau arfFullOriginator de l’en énumération [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) est fixé.</span><span class="sxs-lookup"><span data-stu-id="1c876-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="1c876-115">[out] Le nombre de chars larges dans la valeur de hachage retourné.</span><span class="sxs-lookup"><span data-stu-id="1c876-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="1c876-116">[out] Un pointeur pour les drapeaux qui décrivent les métadonnées appliquées à un assemblage.</span><span class="sxs-lookup"><span data-stu-id="1c876-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="1c876-117">La valeur des drapeaux est une combinaison d’une ou plusieurs valeurs [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="1c876-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c876-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1c876-118">Return Value</span></span>  
 <span data-ttu-id="1c876-119">Cette méthode renvoie S_OK si elle réussit; autrement, il renvoie l’un des codes d’erreur définis dans le fichier d’en-tête Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="1c876-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c876-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1c876-120">Requirements</span></span>  
 <span data-ttu-id="1c876-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c876-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c876-122">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="1c876-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c876-123">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c876-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c876-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c876-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c876-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c876-125">See also</span></span>

- [<span data-ttu-id="1c876-126">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="1c876-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
