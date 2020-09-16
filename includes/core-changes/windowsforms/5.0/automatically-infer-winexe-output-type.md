---
ms.openlocfilehash: 54bee14f6de409550357194e905b6ee5d8ef8f18
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90678995"
---
### <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="457ea-101">OutputType défini sur WinExe pour les applications WPF et WinForms</span><span class="sxs-lookup"><span data-stu-id="457ea-101">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="457ea-102">`OutputType` a automatiquement la valeur `WinExe` pour les applications Windows Presentation Foundation (WPF) et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="457ea-102">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="457ea-103">Lorsque `OutputType` a la valeur `WinExe` , une fenêtre de console ne s’ouvre pas lorsque l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="457ea-103">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

#### <a name="change-description"></a><span data-ttu-id="457ea-104">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="457ea-104">Change description</span></span>

<span data-ttu-id="457ea-105">Dans les versions précédentes de .NET, la valeur spécifiée pour `OutputType` dans le fichier projet est utilisée.</span><span class="sxs-lookup"><span data-stu-id="457ea-105">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="457ea-106">Exemple :</span><span class="sxs-lookup"><span data-stu-id="457ea-106">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="457ea-107">À compter de .NET 5,0, `OutputType` a automatiquement la valeur `WinExe` pour WPF et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="457ea-107">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="457ea-108">Exemple :</span><span class="sxs-lookup"><span data-stu-id="457ea-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

#### <a name="reason-for-change"></a><span data-ttu-id="457ea-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="457ea-109">Reason for change</span></span>

<span data-ttu-id="457ea-110">Il est supposé que la plupart des utilisateurs ne souhaitent pas qu’une fenêtre de console s’ouvre quand une application WPF ou Windows Forms est exécutée.</span><span class="sxs-lookup"><span data-stu-id="457ea-110">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="457ea-111">En outre, à [présent que ces types d’applications utilisent le kit de développement logiciel (SDK) .net](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) au lieu du Windows Desktop SDK, la valeur par défaut correcte est définie.</span><span class="sxs-lookup"><span data-stu-id="457ea-111">In addition, [now that these application types use the .NET SDK](../../../../docs/core/compatibility/wpf.md#winforms-and-wpf-apps-use-microsoftnetsdk) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="457ea-112">De plus, lorsque la prise en charge du ciblage d’iOS et d’Android est ajoutée, il sera plus facile de cibler plusieurs plateformes entre plusieurs plateformes si elles utilisent toutes le même type de sortie.</span><span class="sxs-lookup"><span data-stu-id="457ea-112">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="457ea-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="457ea-113">Version introduced</span></span>

<span data-ttu-id="457ea-114">.NET 5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="457ea-114">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="457ea-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="457ea-115">Recommended action</span></span>

<span data-ttu-id="457ea-116">Aucune action n’est requise de votre part.</span><span class="sxs-lookup"><span data-stu-id="457ea-116">No action is required in your part.</span></span> <span data-ttu-id="457ea-117">Toutefois, si vous souhaitez revenir à l’ancien comportement, affectez à la `DisableWinExeOutputInference` propriété la valeur `true` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="457ea-117">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

#### <a name="category"></a><span data-ttu-id="457ea-118">Category</span><span class="sxs-lookup"><span data-stu-id="457ea-118">Category</span></span>

- <span data-ttu-id="457ea-119">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="457ea-119">Windows Forms</span></span>
- <span data-ttu-id="457ea-120">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="457ea-120">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="457ea-121">API affectées</span><span class="sxs-lookup"><span data-stu-id="457ea-121">Affected APIs</span></span>

<span data-ttu-id="457ea-122">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="457ea-122">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
