---
title: 'Procédure : Effectuer un test de positionnement dans un Viewport3D'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
ms.openlocfilehash: 54d3ee859a50ed348308b083c48f2dd73d312bbe
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106937"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a><span data-ttu-id="715ea-102">Procédure : Effectuer un test de positionnement dans un Viewport3D</span><span class="sxs-lookup"><span data-stu-id="715ea-102">How to: Hit Test in a Viewport3D</span></span>
<span data-ttu-id="715ea-103">Cet exemple montre comment effectuer un test de positionnement pour les visuels 3D <xref:System.Windows.Controls.Viewport3D>dans un.</span><span class="sxs-lookup"><span data-stu-id="715ea-103">This example shows how to hit test for 3D Visuals in a <xref:System.Windows.Controls.Viewport3D>.</span></span>  
  
 <span data-ttu-id="715ea-104">Étant <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> donné que retourne des informations 2D et 3D, il est possible d’itérer au sein des résultats des tests pour lire uniquement les résultats 3D.</span><span class="sxs-lookup"><span data-stu-id="715ea-104">Because <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> returns 2D and 3D information, it is possible to iterate through the test results to read only 3D results.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <span data-ttu-id="715ea-105">Le <xref:System.Windows.Media.HitTestResultBehavior> dans le code suivant détermine la façon dont les résultats du test de positionnement sont traités.</span><span class="sxs-lookup"><span data-stu-id="715ea-105">The <xref:System.Windows.Media.HitTestResultBehavior> in the following code determines how the hit test results are processed.</span></span>  <span data-ttu-id="715ea-106">`UpdateResultInfo`et `UpdateMaterial` sont des méthodes définies localement.</span><span class="sxs-lookup"><span data-stu-id="715ea-106">`UpdateResultInfo` and `UpdateMaterial` are locally defined methods.</span></span>  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
 
