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
ms.openlocfilehash: 9dae3f1403d33aaf3cfb87d17856640548a90b4d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688937"
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="ea76a-102">CreateHistoryReader, fonction</span><span class="sxs-lookup"><span data-stu-id="ea76a-102">CreateHistoryReader Function</span></span>

<span data-ttu-id="ea76a-103">Crée un lecteur d’historique pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ea76a-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea76a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea76a-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea76a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea76a-105">Parameters</span></span>  

 `wzFilePath`  
 <span data-ttu-id="ea76a-106">dans Chemin d’accès du fichier.</span><span class="sxs-lookup"><span data-stu-id="ea76a-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="ea76a-107">à En cas de réussite, contient un pointeur vers le lecteur d’historique.</span><span class="sxs-lookup"><span data-stu-id="ea76a-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea76a-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="ea76a-108">Return Value</span></span>  

 <span data-ttu-id="ea76a-109">Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans WinError. h, en plus des valeurs décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="ea76a-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="ea76a-110">Code de retour</span><span class="sxs-lookup"><span data-stu-id="ea76a-110">Return code</span></span>|<span data-ttu-id="ea76a-111">Description</span><span class="sxs-lookup"><span data-stu-id="ea76a-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ea76a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea76a-112">S_OK</span></span>|<span data-ttu-id="ea76a-113">Indique que la méthode s’est terminée avec succès.</span><span class="sxs-lookup"><span data-stu-id="ea76a-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="ea76a-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ea76a-114">E_INVALIDARG</span></span>|<span data-ttu-id="ea76a-115">Indique que `wzFilePath` ou `ppHistoryReader` sont définis sur une référence null.</span><span class="sxs-lookup"><span data-stu-id="ea76a-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea76a-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ea76a-116">Requirements</span></span>  

 <span data-ttu-id="ea76a-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea76a-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea76a-118">**Bibliothèque :** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="ea76a-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="ea76a-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea76a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea76a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea76a-120">See also</span></span>

- [<span data-ttu-id="ea76a-121">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="ea76a-121">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
