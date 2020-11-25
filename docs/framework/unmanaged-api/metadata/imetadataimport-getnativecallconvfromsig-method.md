---
title: IMetaDataImport::GetNativeCallConvFromSig, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
ms.openlocfilehash: d44ad493a786aaa35150515b7c254965490bd714
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701690"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="baee1-102">IMetaDataImport::GetNativeCallConvFromSig, méthode</span><span class="sxs-lookup"><span data-stu-id="baee1-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>

<span data-ttu-id="baee1-103">Obtient la convention d’appel native pour la méthode représentée par le pointeur de signature spécifié.</span><span class="sxs-lookup"><span data-stu-id="baee1-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baee1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baee1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baee1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="baee1-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="baee1-106">dans Pointeur vers la signature de métadonnées de la méthode pour laquelle retourner la Convention d’appel.</span><span class="sxs-lookup"><span data-stu-id="baee1-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="baee1-107">dans Taille en octets de `pvSig` .</span><span class="sxs-lookup"><span data-stu-id="baee1-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="baee1-108">à Pointeur vers la Convention d’appel native.</span><span class="sxs-lookup"><span data-stu-id="baee1-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baee1-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="baee1-109">Requirements</span></span>  

 <span data-ttu-id="baee1-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baee1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baee1-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="baee1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="baee1-112">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="baee1-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="baee1-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baee1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baee1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baee1-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="baee1-115">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="baee1-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="baee1-116">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="baee1-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
