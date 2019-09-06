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
ms.openlocfilehash: 6eb68f4668c6ea5aa8728a81fac98409896f3fd2
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373273"
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>Procédure : Effectuer un test de positionnement dans un Viewport3D

Cet exemple montre comment effectuer un test de positionnement pour les visuels 3D <xref:System.Windows.Controls.Viewport3D>dans un.

Étant <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> donné que retourne des informations 2D et 3D, il est possible d’itérer au sein des résultats des tests pour lire uniquement les résultats 3D.

[!code-csharp[HitTest3D#HitTest3D3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
[!code-vb[HitTest3D#HitTest3D3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]

Le <xref:System.Windows.Media.HitTestResultBehavior> dans le code suivant détermine la façon dont les résultats du test de positionnement sont traités. `UpdateResultInfo`et `UpdateMaterial` sont des méthodes définies localement.

[!code-csharp[HitTest3D#HitTest3D3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
[!code-vb[HitTest3D#HitTest3D3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]
