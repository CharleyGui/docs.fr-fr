---
title: 'Atténuation : rendu de la fenêtre WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf951ecb955a6597757387de1119267ebc58fdc
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301446"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="a0098-102">Atténuation : rendu de la fenêtre WPF</span><span class="sxs-lookup"><span data-stu-id="a0098-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="a0098-103">Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans.</span><span class="sxs-lookup"><span data-stu-id="a0098-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="a0098-104">Impact</span><span class="sxs-lookup"><span data-stu-id="a0098-104">Impact</span></span>

<span data-ttu-id="a0098-105">En général, le rendu de toute une fenêtre sur plusieurs écrans sans découpage est le comportement attendu.</span><span class="sxs-lookup"><span data-stu-id="a0098-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="a0098-106">Cependant, sur Windows 7 et versions antérieures, les fenêtres WPF sont tronquées lorsqu'elles s'étendent au-delà d'un seul affichage, car le rendu d'une partie de la fenêtre sur le second écran a un impact significatif sur les performances.</span><span class="sxs-lookup"><span data-stu-id="a0098-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="a0098-107">L'impact du rendu des fenêtres WPF sur les écrans sur Windows 8 et versions ultérieures n'est pas précisément quantifiable, car il dépend d'un grand nombre de facteurs.</span><span class="sxs-lookup"><span data-stu-id="a0098-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="a0098-108">Dans certains cas, il peut se produire un impact indésirable sur les performances, en particulier pour les utilisateurs qui exécutent des applications riches en graphisme et dont les fenêtres se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="a0098-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="a0098-109">Dans d'autres cas, vous pouvez simplement vouloir un comportement cohérent entre les versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a0098-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="a0098-110">Atténuation</span><span class="sxs-lookup"><span data-stu-id="a0098-110">Mitigation</span></span>

<span data-ttu-id="a0098-111">Vous pouvez désactiver cette modification et rétablir le comportement précédent de découpage d'une fenêtre WPF lorsqu'elle s'étend au-delà d'un affichage unique.</span><span class="sxs-lookup"><span data-stu-id="a0098-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="a0098-112">Il existe deux façons d'effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="a0098-112">There are two ways to do this:</span></span>

- <span data-ttu-id="a0098-113">En ajoutant l'élément `<EnableMultiMonitorDisplayClipping>` à la section `<appSettings>` du fichier de configuration de votre application, vous pouvez activer ou désactiver ce comportement sur les applications qui s'exécutent sur Windows 8 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a0098-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="a0098-114">Par exemple, la section de configuration suivante désactive le rendu sans découpage :</span><span class="sxs-lookup"><span data-stu-id="a0098-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="a0098-115">Le paramètre de configuration `<EnableMultiMonitorDisplayClipping>` peut avoir l'une des deux valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="a0098-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="a0098-116">`true`, pour activer le découpage des fenêtres selon les limites de l'écran pendant le rendu.</span><span class="sxs-lookup"><span data-stu-id="a0098-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="a0098-117">`false`, pour désactiver le découpage des fenêtres selon les limites de l'écran pendant le rendu.</span><span class="sxs-lookup"><span data-stu-id="a0098-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="a0098-118">En définissant la propriété <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> avec la valeur `true` au démarrage de l'application.</span><span class="sxs-lookup"><span data-stu-id="a0098-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0098-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0098-119">See also</span></span>

- [<span data-ttu-id="a0098-120">Modifications du runtime</span><span class="sxs-lookup"><span data-stu-id="a0098-120">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
