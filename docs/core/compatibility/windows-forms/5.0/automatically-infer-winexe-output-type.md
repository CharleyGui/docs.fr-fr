---
title: 'Modification avec rupture : OutputType défini sur WinExe pour les applications WPF et WinForms'
description: En savoir plus sur la modification avec rupture dans .NET 5,0 où OutputType est automatiquement défini sur WinExe pour les applications Windows Forms.
ms.date: 09/18/2020
ms.openlocfilehash: 072c5b11c8304eb540e176ce9747930789f28505
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761256"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="6be11-103">OutputType défini sur WinExe pour les applications WPF et WinForms</span><span class="sxs-lookup"><span data-stu-id="6be11-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="6be11-104">`OutputType` a automatiquement la valeur `WinExe` pour les applications Windows Presentation Foundation (WPF) et Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6be11-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="6be11-105">Lorsque `OutputType` a la valeur `WinExe` , une fenêtre de console ne s’ouvre pas lorsque l’application est exécutée.</span><span class="sxs-lookup"><span data-stu-id="6be11-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="6be11-106">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="6be11-106">Change description</span></span>

<span data-ttu-id="6be11-107">Dans les versions précédentes de .NET, la valeur spécifiée pour `OutputType` dans le fichier projet est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6be11-107">In previous versions of .NET, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="6be11-108">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6be11-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="6be11-109">À compter de .NET 5,0, `OutputType` a automatiquement la valeur `WinExe` pour WPF et les applications Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6be11-109">Starting in .NET 5.0, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps.</span></span> <span data-ttu-id="6be11-110">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6be11-110">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a><span data-ttu-id="6be11-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="6be11-111">Reason for change</span></span>

<span data-ttu-id="6be11-112">Il est supposé que la plupart des utilisateurs ne souhaitent pas qu’une fenêtre de console s’ouvre quand une application WPF ou Windows Forms est exécutée.</span><span class="sxs-lookup"><span data-stu-id="6be11-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="6be11-113">En outre, à [présent que ces types d’applications utilisent le kit de développement logiciel (SDK) .net](sdk-and-target-framework-change.md) au lieu du Windows Desktop SDK, la valeur par défaut correcte est définie.</span><span class="sxs-lookup"><span data-stu-id="6be11-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="6be11-114">De plus, lorsque la prise en charge du ciblage d’iOS et d’Android est ajoutée, il sera plus facile de cibler plusieurs plateformes entre plusieurs plateformes si elles utilisent toutes le même type de sortie.</span><span class="sxs-lookup"><span data-stu-id="6be11-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="6be11-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6be11-115">Version introduced</span></span>

<span data-ttu-id="6be11-116">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6be11-116">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6be11-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6be11-117">Recommended action</span></span>

<span data-ttu-id="6be11-118">Aucune action n’est requise de votre part.</span><span class="sxs-lookup"><span data-stu-id="6be11-118">No action is required in your part.</span></span> <span data-ttu-id="6be11-119">Toutefois, si vous souhaitez revenir à l’ancien comportement, affectez à la `DisableWinExeOutputInference` propriété la valeur `true` dans votre fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6be11-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="6be11-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="6be11-120">Affected APIs</span></span>

<span data-ttu-id="6be11-121">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="6be11-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
