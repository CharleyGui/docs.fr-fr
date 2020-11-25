---
title: IMetaDataImport::GetTypeSpecFromToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: 62495aa4280bb1799af09fea2e550ae6107e09e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729146"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="f7979-102">IMetaDataImport::GetTypeSpecFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="f7979-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>

<span data-ttu-id="f7979-103">Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="f7979-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7979-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7979-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7979-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7979-105">Parameters</span></span>  

 `typespec`  
 <span data-ttu-id="f7979-106">dans Jeton TypeSpec associé à la signature de métadonnées demandée.</span><span class="sxs-lookup"><span data-stu-id="f7979-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="f7979-107">à Pointeur vers la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="f7979-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="f7979-108">à Taille, en octets, de la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f7979-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7979-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="f7979-109">Return Value</span></span>  

 <span data-ttu-id="f7979-110">HRESULT qui indique la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="f7979-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="f7979-111">Les échecs peuvent être testés à l’aide de la macro FAILed.</span><span class="sxs-lookup"><span data-stu-id="f7979-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7979-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7979-112">Requirements</span></span>  

 <span data-ttu-id="f7979-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7979-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7979-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f7979-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7979-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7979-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7979-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7979-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7979-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7979-117">See also</span></span>

- [<span data-ttu-id="f7979-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f7979-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f7979-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f7979-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
