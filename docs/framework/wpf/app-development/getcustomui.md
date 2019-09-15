---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991375"
---
# <a name="getcustomui"></a><span data-ttu-id="90d4d-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="90d4d-102">GetCustomUI</span></span>
<span data-ttu-id="90d4d-103">Appelé par PresentationHost. exe pour recevoir des messages de progression et d’erreur personnalisés de l’hôte, s’il est implémenté.</span><span class="sxs-lookup"><span data-stu-id="90d4d-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90d4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="90d4d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90d4d-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="90d4d-106">à Pointeur vers l’assembly qui contient l’interface utilisateur de la progression fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="90d4d-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="90d4d-107">à Nom de la classe qui est l’interface utilisateur de la progression fournie par l’hôte, [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] de préférence <xref:System.Windows.Controls.Page> un fichier avec est son élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="90d4d-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="90d4d-108">Cette classe réside dans l’assembly spécifié par `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="90d4d-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="90d4d-109">à Pointeur vers l’assembly qui contient l’interface utilisateur d’erreur fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="90d4d-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="90d4d-110">à Nom de la classe qui est l’interface utilisateur d’erreur fournie par l’hôte, de préférence un fichier <xref:System.Windows.Controls.Page> XAML avec est son élément de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="90d4d-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="90d4d-111">Cette classe réside dans l’assembly spécifié par `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="90d4d-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="90d4d-112">Valeur de propriété/valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90d4d-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="90d4d-113">HRESULT : Ignoré.</span><span class="sxs-lookup"><span data-stu-id="90d4d-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90d4d-114">Notes</span><span class="sxs-lookup"><span data-stu-id="90d4d-114">Remarks</span></span>  
 <span data-ttu-id="90d4d-115">Une application hôte peut avoir un thème spécifique auquel les interfaces utilisateur par défaut de PresentationHost. exe peuvent ne pas se conformer.</span><span class="sxs-lookup"><span data-stu-id="90d4d-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="90d4d-116">Si c’est le cas, l’application hôte peut implémenter [GetCustomUI](getcustomui.md) pour retourner les interfaces utilisateur de progression et d’erreur à PresentationHost. exe.</span><span class="sxs-lookup"><span data-stu-id="90d4d-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="90d4d-117">PresentationHost. exe appellera toujours [GetCustomUI](getcustomui.md) avant d’utiliser ses interfaces utilisateur par défaut.</span><span class="sxs-lookup"><span data-stu-id="90d4d-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="90d4d-118">Cette fonction est appelée une fois pendant l’initialisation de PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="90d4d-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d4d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90d4d-119">See also</span></span>

- [<span data-ttu-id="90d4d-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="90d4d-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
