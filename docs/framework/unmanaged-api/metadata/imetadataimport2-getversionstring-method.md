---
title: IMetaDataImport2::GetVersionString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d500584afd608f79e41e932be259d29ae51db2db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781583"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="e0f61-102">IMetaDataImport2::GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="e0f61-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="e0f61-103">Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="e0f61-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0f61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0f61-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="e0f61-106">[out] Un tableau pour stocker la chaîne qui spécifie la version.</span><span class="sxs-lookup"><span data-stu-id="e0f61-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="e0f61-107">[in] La taille, en caractères larges, de la `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="e0f61-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="e0f61-108">[out] Le nombre de caractères larges, y compris une marque de fin null, retournés dans le `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="e0f61-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0f61-109">Notes</span><span class="sxs-lookup"><span data-stu-id="e0f61-109">Remarks</span></span>  
 <span data-ttu-id="e0f61-110">Le `GetVersionString` méthode obtient la version propre à la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="e0f61-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="e0f61-111">Si l’étendue n’a jamais été enregistré, il n’aura pas d’une version propre à, et une chaîne vide est retournée.</span><span class="sxs-lookup"><span data-stu-id="e0f61-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0f61-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0f61-112">Requirements</span></span>  
 <span data-ttu-id="e0f61-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0f61-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f61-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e0f61-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0f61-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0f61-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0f61-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f61-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f61-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0f61-117">See also</span></span>

- [<span data-ttu-id="e0f61-118">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e0f61-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="e0f61-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e0f61-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
