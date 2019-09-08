---
title: CreateHistoryReader, fonction
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795367"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="d5499-102">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="d5499-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="d5499-103">Crée un lecteur d’historique pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="d5499-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5499-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5499-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5499-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d5499-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="d5499-106">dans Chemin d’accès du fichier.</span><span class="sxs-lookup"><span data-stu-id="d5499-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="d5499-107">à En cas de réussite, contient un pointeur vers le lecteur d’historique.</span><span class="sxs-lookup"><span data-stu-id="d5499-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5499-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d5499-108">Return Value</span></span>  
 <span data-ttu-id="d5499-109">Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans WinError. h, en plus des valeurs décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d5499-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="d5499-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="d5499-110">Return code</span></span>|<span data-ttu-id="d5499-111">Description</span><span class="sxs-lookup"><span data-stu-id="d5499-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d5499-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d5499-112">S_OK</span></span>|<span data-ttu-id="d5499-113">Indique que la méthode s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="d5499-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="d5499-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d5499-114">E_INVALIDARG</span></span>|<span data-ttu-id="d5499-115">Indique que `wzFilePath` ou `ppHistoryReader` sont définis sur une référence null.</span><span class="sxs-lookup"><span data-stu-id="d5499-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d5499-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d5499-116">Requirements</span></span>  
 <span data-ttu-id="d5499-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5499-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5499-118">**Bibliothèque** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="d5499-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="d5499-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5499-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5499-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5499-120">See also</span></span>

- [<span data-ttu-id="d5499-121">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="d5499-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
