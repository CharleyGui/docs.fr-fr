---
title: IMetaDataConverter::GetTypeLibFromMetaData, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataConverter.GetTypeLibFromMetaData
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataConverter::GetTypeLibFromMetaData
helpviewer_keywords:
- GetTypeLibFromMetaData method [.NET Framework metadata]
- IMetaDataConverter::GetTypeLibFromMetaData method [.NET Framework metadata]
ms.assetid: 90eab7b3-1fae-4af4-8bce-f7bc0e188a99
topic_type:
- apiref
ms.openlocfilehash: eed8661f8885ca16492ab336a599b5290057843a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714599"
---
# <a name="imetadataconvertergettypelibfrommetadata-method"></a><span data-ttu-id="1c18e-102">IMetaDataConverter::GetTypeLibFromMetaData, méthode</span><span class="sxs-lookup"><span data-stu-id="1c18e-102">IMetaDataConverter::GetTypeLibFromMetaData Method</span></span>

<span data-ttu-id="1c18e-103">Obtient un pointeur vers une `ITypeLib` instance de qui représente la bibliothèque de types qui a la bibliothèque et les noms de modules spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1c18e-103">Gets a pointer to an `ITypeLib` instance that represents the type library that has the specified library and module names.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c18e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c18e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLibFromMetaData (  
    [in]  BSTR     strModule,
    [in]  BSTR     strTlbName,
    [out] ITypeLib **ppITL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c18e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c18e-105">Parameters</span></span>  

 `strModule`  
 <span data-ttu-id="1c18e-106">dans Nom du module de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="1c18e-106">[in] The name of the type library's module.</span></span>  
  
 `strTlbName`  
 <span data-ttu-id="1c18e-107">dans Nom de la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="1c18e-107">[in] The name of the type library.</span></span>  
  
 `ppITL`  
 <span data-ttu-id="1c18e-108">à Pointeur vers un emplacement qui reçoit l’adresse de l' `ITypeLib` instance qui représente la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="1c18e-108">[out] A pointer to a location that receives the address of the `ITypeLib` instance that represents the type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c18e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c18e-109">Requirements</span></span>  

 <span data-ttu-id="1c18e-110">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c18e-110">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c18e-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1c18e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1c18e-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c18e-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1c18e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c18e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c18e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c18e-114">See also</span></span>

- [<span data-ttu-id="1c18e-115">IMetaDataConverter, interface</span><span class="sxs-lookup"><span data-stu-id="1c18e-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)
