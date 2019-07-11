---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60390fecad15dbb2c453453fa8c35556b5db6b54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777716"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="61c89-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="61c89-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="61c89-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="61c89-103">This method is not implemented.</span></span> <span data-ttu-id="61c89-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="61c89-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61c89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61c89-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61c89-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="61c89-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="61c89-107">[in] Pointeur vers un [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface qui fournit les informations de type sur lequel ouvrir la portée.</span><span class="sxs-lookup"><span data-stu-id="61c89-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="61c89-108">[in] Les indicateurs de mode d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="61c89-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="61c89-109">[in] L’interface souhaitée.</span><span class="sxs-lookup"><span data-stu-id="61c89-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="61c89-110">[out] Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="61c89-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61c89-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="61c89-111">Requirements</span></span>  
 <span data-ttu-id="61c89-112">**Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61c89-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61c89-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="61c89-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61c89-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61c89-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61c89-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61c89-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61c89-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61c89-116">See also</span></span>

- [<span data-ttu-id="61c89-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="61c89-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="61c89-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="61c89-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
