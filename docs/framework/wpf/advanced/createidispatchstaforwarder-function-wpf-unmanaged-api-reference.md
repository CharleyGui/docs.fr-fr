---
title: CreateIDispatchSTAForwarder Function - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174717"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="242c4-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span><span class="sxs-lookup"><span data-stu-id="242c4-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="242c4-103">Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="242c4-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="242c4-104">Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fils et des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="242c4-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="242c4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="242c4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="242c4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="242c4-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="242c4-107">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="242c4-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="242c4-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="242c4-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="242c4-109">Un pointeur `IDispatch` à une interface.</span><span class="sxs-lookup"><span data-stu-id="242c4-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="242c4-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="242c4-110">ppForwarder</span></span>  
 <span data-ttu-id="242c4-111">Un pointeur à `IDispatch` l’adresse d’une interface.</span><span class="sxs-lookup"><span data-stu-id="242c4-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="242c4-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="242c4-112">Requirements</span></span>  
 <span data-ttu-id="242c4-113">**Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="242c4-113">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="242c4-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="242c4-114">**DLL:**</span></span>  
  
 <span data-ttu-id="242c4-115">Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="242c4-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="242c4-116">Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="242c4-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="242c4-117">**Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="242c4-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242c4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="242c4-118">See also</span></span>

- [<span data-ttu-id="242c4-119">Informations de référence sur les API non managées WPF</span><span class="sxs-lookup"><span data-stu-id="242c4-119">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
