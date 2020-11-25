---
title: IMetaDataError::OnError, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataError.OnError
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataError::OnError
helpviewer_keywords:
- IMetaDataError::OnError method [.NET Framework metadata]
- OnError method, IMetaDataError interface [.NET Framework metadata]
ms.assetid: c1e744b8-a6fb-4d9c-a971-8babc875d8f0
topic_type:
- apiref
ms.openlocfilehash: 6f6e531c99d341eba39939a184d2424256d9e155
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701872"
---
# <a name="imetadataerroronerror-method"></a><span data-ttu-id="56757-102">IMetaDataError::OnError, méthode</span><span class="sxs-lookup"><span data-stu-id="56757-102">IMetaDataError::OnError Method</span></span>

<span data-ttu-id="56757-103">Fournit une notification des erreurs qui se produisent pendant la fusion des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="56757-103">Provides notification of errors that occur during the metadata merge.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56757-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56757-104">Syntax</span></span>  
  
```cpp  
HRESULT OnError (  
    [in] HRESULT   hrError,
    [in] mdToken   token  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56757-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56757-105">Parameters</span></span>  

 `hrError`  
 <span data-ttu-id="56757-106">dans Valeur d’erreur HRESULT retournée à la méthode d’appel.</span><span class="sxs-lookup"><span data-stu-id="56757-106">[in] The HRESULT error value returned to the calling method.</span></span>  
  
 `token`  
 <span data-ttu-id="56757-107">dans Jeton de métadonnées de l’objet de code qui a été fusionné lorsque l’erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="56757-107">[in] The metadata token of the code object that was being merged when the error occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56757-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56757-108">Requirements</span></span>  

 <span data-ttu-id="56757-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56757-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56757-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56757-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56757-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56757-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56757-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56757-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56757-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56757-113">See also</span></span>

- [<span data-ttu-id="56757-114">IMetaDataError, interface</span><span class="sxs-lookup"><span data-stu-id="56757-114">IMetaDataError Interface</span></span>](imetadataerror-interface.md)
