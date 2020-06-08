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
ms.openlocfilehash: 43e9671afa92d36966e51bbdc630db4a9d9083b7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503500"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="a8cc0-102">IMetaDataImport::GetTypeSpecFromToken, méthode</span><span class="sxs-lookup"><span data-stu-id="a8cc0-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="a8cc0-103">Obtient la signature de métadonnées binaires de la spécification de type représentée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8cc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8cc0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8cc0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a8cc0-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="a8cc0-106">dans Jeton TypeSpec associé à la signature de métadonnées demandée.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="a8cc0-107">à Pointeur vers la signature de métadonnées binaires.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="a8cc0-108">à Taille, en octets, de la signature de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8cc0-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a8cc0-109">Return Value</span></span>  
 <span data-ttu-id="a8cc0-110">HRESULT qui indique la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="a8cc0-111">Les échecs peuvent être testés à l’aide de la macro FAILed.</span><span class="sxs-lookup"><span data-stu-id="a8cc0-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8cc0-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a8cc0-112">Requirements</span></span>  
 <span data-ttu-id="a8cc0-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8cc0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8cc0-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a8cc0-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8cc0-115">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8cc0-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8cc0-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8cc0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cc0-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8cc0-117">See also</span></span>

- [<span data-ttu-id="a8cc0-118">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="a8cc0-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a8cc0-119">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="a8cc0-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
