---
ms.openlocfilehash: c9720f51e40ada4cd2cf6997ba7006a232893553
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702463"
---
### <a name="removed-status-bar-controls"></a><span data-ttu-id="feaeb-101">Contrôles de barre d’État supprimés</span><span class="sxs-lookup"><span data-stu-id="feaeb-101">Removed status bar controls</span></span>

<span data-ttu-id="feaeb-102">À compter de .NET 5,0 Preview 1, certains contrôles de Windows Forms ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="feaeb-102">Starting in .NET 5.0 Preview 1, some Windows Forms controls are no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="feaeb-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="feaeb-103">Change description</span></span>

<span data-ttu-id="feaeb-104">À compter de .NET 5,0 Preview 1, certains des contrôles de Windows Forms liés à la barre d’État ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="feaeb-104">Starting with .NET 5.0 Preview 1, some of the status bar-related Windows Forms controls are no longer available.</span></span> <span data-ttu-id="feaeb-105">Les contrôles de remplacement qui offrent une meilleure conception et une meilleure prise en charge ont été introduits dans .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="feaeb-105">Replacement controls that have better design and support were introduced in .NET Framework 2.0.</span></span> <span data-ttu-id="feaeb-106">Les contrôles déconseillés ont été précédemment supprimés des boîtes à outils du concepteur, mais ils étaient toujours disponibles pour être utilisés.</span><span class="sxs-lookup"><span data-stu-id="feaeb-106">The deprecated controls were previously removed from designer toolboxes but were still available to be used.</span></span> <span data-ttu-id="feaeb-107">Ils ont été complètement supprimés.</span><span class="sxs-lookup"><span data-stu-id="feaeb-107">Now, they have been completely removed.</span></span>

<span data-ttu-id="feaeb-108">Les types suivants ne sont plus disponibles :</span><span class="sxs-lookup"><span data-stu-id="feaeb-108">The following types are no longer available:</span></span>

* `StatusBar`
* `StatusBarDrawItemEventArgs`
* `StatusBarDrawItemEventHandler`
* `StatusBarPanel`
* `StatusBarPanelAutoSize`
* `StatusBarPanelBorderStyle`
* `StatusBarPanelClickEventArgs`
* `StatusBarPanelClickEventHandler`
* `StatusBarPanelStyle`

#### <a name="version-introduced"></a><span data-ttu-id="feaeb-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="feaeb-109">Version introduced</span></span>

<span data-ttu-id="feaeb-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="feaeb-110">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="feaeb-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="feaeb-111">Recommended action</span></span>

<span data-ttu-id="feaeb-112">Accédez aux API de remplacement de ces contrôles et à leurs scénarios :</span><span class="sxs-lookup"><span data-stu-id="feaeb-112">Move to the replacement APIs for these controls and their scenarios:</span></span>

| <span data-ttu-id="feaeb-113">Ancien contrôle (API)</span><span class="sxs-lookup"><span data-stu-id="feaeb-113">Old Control (API)</span></span> | <span data-ttu-id="feaeb-114">Remplacement recommandé</span><span class="sxs-lookup"><span data-stu-id="feaeb-114">Recommended Replacement</span></span>                          |
|-------------------|--------------------------------------------------|
| <span data-ttu-id="feaeb-115">StatusBar</span><span class="sxs-lookup"><span data-stu-id="feaeb-115">StatusBar</span></span>         | <xref:System.Windows.Forms.StatusStrip>          |
| <span data-ttu-id="feaeb-116">StatusBarPanel</span><span class="sxs-lookup"><span data-stu-id="feaeb-116">StatusBarPanel</span></span>    | <xref:System.Windows.Forms.ToolStripStatusLabel> |

#### <a name="category"></a><span data-ttu-id="feaeb-117">Category</span><span class="sxs-lookup"><span data-stu-id="feaeb-117">Category</span></span>

<span data-ttu-id="feaeb-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="feaeb-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="feaeb-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="feaeb-119">Affected APIs</span></span>

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

#### Affected APIs

- `T:System.Windows.Forms.StatusBar`
- `T:System.Windows.Forms.StatusBarDrawItemEventArgs`
- `T:System.Windows.Forms.StatusBarDrawItemEventHandler`
- `T:System.Windows.Forms.StatusBarPanel`
- `T:System.Windows.Forms.StatusBarPanelAutoSize`
- `T:System.Windows.Forms.StatusBarPanelBorderStyle`
- `T:System.Windows.Forms.StatusBarPanelClickEventArgs`
- `T:System.Windows.Forms.StatusBarPanelClickEventHandler`
- `T:System.Windows.Forms.StatusBarPanelStyle` 

-->
