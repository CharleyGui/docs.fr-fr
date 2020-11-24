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
ms.openlocfilehash: 6056a64b354f69ce39692173da01892870fba9e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682846"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="e17c0-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="e17c0-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>

<span data-ttu-id="e17c0-103">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="e17c0-103">This method is not implemented.</span></span> <span data-ttu-id="e17c0-104">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="e17c0-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e17c0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e17c0-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e17c0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e17c0-106">Parameters</span></span>  

 `pITI`  
 <span data-ttu-id="e17c0-107">dans Pointeur vers une interface [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) qui fournit les informations de type sur lesquelles ouvrir la portée.</span><span class="sxs-lookup"><span data-stu-id="e17c0-107">[in] Pointer to an [ITypeInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="e17c0-108">dans Indicateurs du mode d’ouverture.</span><span class="sxs-lookup"><span data-stu-id="e17c0-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="e17c0-109">dans Interface souhaitée.</span><span class="sxs-lookup"><span data-stu-id="e17c0-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="e17c0-110">à Pointeur vers un pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="e17c0-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e17c0-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e17c0-111">Requirements</span></span>  

 <span data-ttu-id="e17c0-112">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e17c0-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e17c0-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e17c0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e17c0-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e17c0-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e17c0-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e17c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e17c0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e17c0-116">See also</span></span>

- [<span data-ttu-id="e17c0-117">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="e17c0-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="e17c0-118">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="e17c0-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
