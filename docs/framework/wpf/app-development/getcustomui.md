---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: e9ef32912c2afb3c99e46e1e14bb3daa5a2e99af
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005713"
---
# <a name="getcustomui"></a><span data-ttu-id="62875-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="62875-102">GetCustomUI</span></span>
<span data-ttu-id="62875-103">Appelé par PresentationHost. exe pour recevoir des messages de progression et d’erreur personnalisés de l’hôte, s’il est implémenté.</span><span class="sxs-lookup"><span data-stu-id="62875-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62875-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62875-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="62875-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="62875-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="62875-106">à Pointeur vers l’assembly qui contient l’interface utilisateur de la progression fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="62875-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="62875-107">à Nom de la classe qui est l’interface utilisateur de la progression fournie par l’hôte, de préférence un fichier XAML avec <xref:System.Windows.Controls.Page> est son élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="62875-107">[out] The name of the class that is the host-supplied progress user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="62875-108">Cette classe réside dans l’assembly spécifié par `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="62875-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="62875-109">à Pointeur vers l’assembly qui contient l’interface utilisateur d’erreur fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="62875-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="62875-110">à Nom de la classe qui est l’interface utilisateur d’erreur fournie par l’hôte, de préférence un fichier XAML avec <xref:System.Windows.Controls.Page> est son élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="62875-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="62875-111">Cette classe réside dans l’assembly spécifié par `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="62875-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="62875-112">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="62875-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="62875-113">HRESULT : Ignoré.</span><span class="sxs-lookup"><span data-stu-id="62875-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62875-114">Notes</span><span class="sxs-lookup"><span data-stu-id="62875-114">Remarks</span></span>  
 <span data-ttu-id="62875-115">Une application hôte peut avoir un thème spécifique auquel les interfaces utilisateur par défaut de PresentationHost. exe peuvent ne pas se conformer.</span><span class="sxs-lookup"><span data-stu-id="62875-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="62875-116">Si c’est le cas, l’application hôte peut implémenter [GetCustomUI](getcustomui.md) pour retourner les interfaces utilisateur de progression et d’erreur à PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="62875-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="62875-117">PresentationHost. exe appellera toujours [GetCustomUI](getcustomui.md) avant d’utiliser ses interfaces utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="62875-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="62875-118">Cette fonction est appelée une fois pendant l’initialisation de PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="62875-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62875-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62875-119">See also</span></span>

- [<span data-ttu-id="62875-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="62875-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
