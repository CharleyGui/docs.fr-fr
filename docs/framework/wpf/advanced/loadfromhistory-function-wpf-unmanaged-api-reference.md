---
title: LoadDeHistory Function - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141573"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="c5c31-102">LoadDeHistory Function (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="c5c31-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="c5c31-103">Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="c5c31-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="c5c31-104">Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="c5c31-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c31-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5c31-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c31-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5c31-106">Parameters</span></span>  
 <span data-ttu-id="c5c31-107">pHistoryStream (en anglais seulement)</span><span class="sxs-lookup"><span data-stu-id="c5c31-107">pHistoryStream</span></span>  
 <span data-ttu-id="c5c31-108">Un pointeur à un flux d’informations d’histoire.</span><span class="sxs-lookup"><span data-stu-id="c5c31-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="c5c31-109">pBindCtx (en)</span><span class="sxs-lookup"><span data-stu-id="c5c31-109">pBindCtx</span></span>  
 <span data-ttu-id="c5c31-110">Un pointeur à un contexte de liaison.</span><span class="sxs-lookup"><span data-stu-id="c5c31-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c31-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c5c31-111">Requirements</span></span>  
 <span data-ttu-id="c5c31-112">**Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5c31-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c31-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="c5c31-113">**DLL:**</span></span>  
  
 <span data-ttu-id="c5c31-114">Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="c5c31-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="c5c31-115">Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="c5c31-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="c5c31-116">**Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c31-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c31-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5c31-117">See also</span></span>

- [<span data-ttu-id="c5c31-118">Informations de référence sur les API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="c5c31-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
