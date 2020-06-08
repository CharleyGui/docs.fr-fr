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
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490403"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="cf879-102">IMetaDataImport2::GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="cf879-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="cf879-103">Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="cf879-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf879-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf879-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf879-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf879-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="cf879-106">à Tableau pour stocker la chaîne qui spécifie la version.</span><span class="sxs-lookup"><span data-stu-id="cf879-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="cf879-107">dans Taille, en caractères larges, du `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="cf879-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="cf879-108">à Nombre de caractères larges, y compris un terminateur null, retournés dans le `pwzBuf` tableau.</span><span class="sxs-lookup"><span data-stu-id="cf879-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf879-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf879-109">Remarks</span></span>  
 <span data-ttu-id="cf879-110">La `GetVersionString` méthode obtient la version intégrée de la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf879-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="cf879-111">Si l’étendue n’a jamais été enregistrée, elle n’a pas de version intégrée et une chaîne vide est retournée.</span><span class="sxs-lookup"><span data-stu-id="cf879-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf879-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf879-112">Requirements</span></span>  
 <span data-ttu-id="cf879-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf879-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf879-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cf879-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf879-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf879-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf879-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf879-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf879-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf879-117">See also</span></span>

- [<span data-ttu-id="cf879-118">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="cf879-118">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="cf879-119">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="cf879-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
