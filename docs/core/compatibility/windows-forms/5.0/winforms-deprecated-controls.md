---
title: 'Modification avec rupture : suppression des contrôles de barre d’État'
description: Découvrez la modification avec rupture dans .NET 5,0 où certains contrôles de Windows Forms ne sont plus disponibles.
ms.date: 07/18/2020
ms.openlocfilehash: 70aaa20f3fee1f4c342c4d9e547b0658aaf533b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761142"
---
# <a name="removed-status-bar-controls"></a><span data-ttu-id="a18b1-103">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="a18b1-103">Removed status bar controls</span></span>

<span data-ttu-id="a18b1-104">À compter de .NET 5,0, certains contrôles de Windows Forms ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="a18b1-104">Starting in .NET 5.0, some Windows Forms controls are no longer available.</span></span>

## <a name="change-description"></a><span data-ttu-id="a18b1-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="a18b1-105">Change description</span></span>

<span data-ttu-id="a18b1-106">À compter de .NET 5,0, certains des contrôles Windows Forms liés à la barre d’État ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="a18b1-106">Starting with .NET 5.0, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="a18b1-107">Les contrôles de remplacement qui offrent une meilleure conception et une meilleure prise en charge ont été introduits dans .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="a18b1-107">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="a18b1-108">Les contrôles déconseillés ont été précédemment supprimés des boîtes à outils du concepteur, mais ils étaient toujours disponibles pour être utilisés.</span><span class="sxs-lookup"><span data-stu-id="a18b1-108">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="a18b1-109">Ils ont été complètement supprimés.</span><span class="sxs-lookup"><span data-stu-id="a18b1-109">Now, they have been completely removed.</span></span>

<span data-ttu-id="a18b1-110">Les types suivants ne sont plus disponibles :</span><span class="sxs-lookup"><span data-stu-id="a18b1-110">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

## <a name="version-introduced"></a><span data-ttu-id="a18b1-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a18b1-111">Version introduced</span></span>

<span data-ttu-id="a18b1-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a18b1-112">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a18b1-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a18b1-113">Recommended action</span></span>

<span data-ttu-id="a18b1-114">Accédez aux API de remplacement de ces contrôles et à leurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="a18b1-114">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="a18b1-115">Ancien contrôle (API)</span><span class="sxs-lookup"><span data-stu-id="a18b1-115">Old Control (API)</span></span> | <span data-ttu-id="a18b1-116">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="a18b1-116">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="a18b1-117">StatusBar</span><span class="sxs-lookup"><span data-stu-id="a18b1-117">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="a18b1-118">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="a18b1-118">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

## <a name="affected-apis"></a><span data-ttu-id="a18b1-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="a18b1-119">Affected APIs</span></span>

- <xref:System.Windows.Forms.StatusBar?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarDrawItemEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanel?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelAutoSize?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelBorderStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventArgs?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelClickEventHandler?displayProperty=fullName>
- <xref:System.Windows.Forms.StatusBarPanelStyle?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle`

### Category

Windows Forms

-->
