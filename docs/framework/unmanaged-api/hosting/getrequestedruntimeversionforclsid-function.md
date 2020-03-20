---
title: GetRequestedRuntimeVersionForCLSID, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178114"
---
# <a name="getrequestedruntimeversionforclsid-function"></a><span data-ttu-id="79176-102">GetRequestedRuntimeVersionForCLSID, fonction</span><span class="sxs-lookup"><span data-stu-id="79176-102">GetRequestedRuntimeVersionForCLSID Function</span></span>
<span data-ttu-id="79176-103">Obtient les informations appropriées de version de l’heure courante `CLSID`(CLR) pour la classe avec le spécifié .</span><span class="sxs-lookup"><span data-stu-id="79176-103">Gets the appropriate common language runtime (CLR) version information for the class with the specified `CLSID`.</span></span>  
  
 <span data-ttu-id="79176-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="79176-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79176-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79176-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79176-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79176-106">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="79176-107">[dans]  Le `CLSID` composant.</span><span class="sxs-lookup"><span data-stu-id="79176-107">[in]  The `CLSID` of the component.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="79176-108">[out]  Un tampon qui contient la chaîne de numéro de version une fois terminé.</span><span class="sxs-lookup"><span data-stu-id="79176-108">[out]  A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="79176-109">[dans]  La taille, en caractères `pVersion` larges, du tampon.</span><span class="sxs-lookup"><span data-stu-id="79176-109">[in]  The size, in wide characters, of the `pVersion` buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="79176-110">[out] La longueur, dans les octets, du tampon retourné.</span><span class="sxs-lookup"><span data-stu-id="79176-110">[out] The length, in bytes, of the returned buffer.</span></span>  
  
 `dwResolutionFlags`  
 <span data-ttu-id="79176-111">[dans]  Une des valeurs CLSID_RESOLUTION_FLAGS.</span><span class="sxs-lookup"><span data-stu-id="79176-111">[in]  One of the CLSID_RESOLUTION_FLAGS values.</span></span> <span data-ttu-id="79176-112">Les valeurs suivantes sont admises :</span><span class="sxs-lookup"><span data-stu-id="79176-112">The following values are supported:</span></span>  
  
- <span data-ttu-id="79176-113">CLSID_RESOLUTION_DEFAULT: (0x0) précise que le comportement interop par défaut doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="79176-113">CLSID_RESOLUTION_DEFAULT: (0x0) Specifies that default interop behavior should be used.</span></span>  
  
- <span data-ttu-id="79176-114">CLSID_RESOLUTION_REGISTERED: (0x1) précise que le registre doit être recherché et la politique cale doit être appliquée.</span><span class="sxs-lookup"><span data-stu-id="79176-114">CLSID_RESOLUTION_REGISTERED: (0x1) Specifies that the registry should be searched and shim policy should be applied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79176-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79176-115">Return Value</span></span>  
  
|<span data-ttu-id="79176-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="79176-116">HRESULT</span></span>|<span data-ttu-id="79176-117">Description</span><span class="sxs-lookup"><span data-stu-id="79176-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="79176-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="79176-118">S_OK</span></span>|<span data-ttu-id="79176-119">La fonction est revenue avec succès.</span><span class="sxs-lookup"><span data-stu-id="79176-119">The function returned successfully.</span></span>|  
|<span data-ttu-id="79176-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="79176-120">E_INVALIDARG</span></span>|<span data-ttu-id="79176-121">L’un des paramètres a un type ou un format invalide.</span><span class="sxs-lookup"><span data-stu-id="79176-121">One of the parameters has an invalid type or format.</span></span>|  
|<span data-ttu-id="79176-122">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="79176-122">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="79176-123">Le `pVersion` tampon n’est pas assez grand pour tenir la chaîne de version entière.</span><span class="sxs-lookup"><span data-stu-id="79176-123">The `pVersion` buffer is not large enough to hold the entire version string.</span></span>|  
|<span data-ttu-id="79176-124">REGDB_E_CLASSNOTREG</span><span class="sxs-lookup"><span data-stu-id="79176-124">REGDB_E_CLASSNOTREG</span></span>|<span data-ttu-id="79176-125">Il n’y a `CLSID`pas de classe enregistrée auprès des spécifiés .</span><span class="sxs-lookup"><span data-stu-id="79176-125">There is no class registered with the specified `CLSID`.</span></span>|  
|<span data-ttu-id="79176-126">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="79176-126">E_POINTER</span></span>|<span data-ttu-id="79176-127">`dwLength`est nul, `cchBuffer` ou est assez grand pour `pVersion` tenir la chaîne de version, mais est nul.</span><span class="sxs-lookup"><span data-stu-id="79176-127">`dwLength` is null, or `cchBuffer` is large enough to hold the version string, but `pVersion` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="79176-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79176-128">Requirements</span></span>  
 <span data-ttu-id="79176-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79176-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79176-130">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="79176-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="79176-131">**.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79176-131">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79176-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79176-132">See also</span></span>

- [<span data-ttu-id="79176-133">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="79176-133">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
