---
title: Multithread dans les contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: 79832e12a10f02c909d2a28270594bcb4ea68656
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742145"
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithreading dans les contrôles Windows Forms
Dans de nombreuses applications, vous pouvez rendre votre interface utilisateur plus réactive en effectuant des opérations qui prennent du temps sur un autre thread. Un certain nombre d’outils sont disponibles pour le multithreading de vos contrôles de Windows Forms, y compris l’espace de noms <xref:System.Threading>, la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> et le composant `BackgroundWorker`.  
  
> [!NOTE]
> Le composant `BackgroundWorker` remplace et ajoute des fonctionnalités à l’espace de noms <xref:System.Threading> et à la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> ; Toutefois, ceux-ci sont conservés pour la compatibilité descendante et l’utilisation ultérieure, si vous le souhaitez. Pour plus d’informations, consultez [vue d’ensemble du composant BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour faire des appels thread-safe aux contrôles Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Montre comment effectuer des appels thread-safe pour Windows Forms contrôles.  
  
 [Guide pratique pour utiliser un thread d'arrière-plan pour rechercher des fichiers](how-to-use-a-background-thread-to-search-for-files.md)  
 Montre comment utiliser l’espace de noms <xref:System.Threading> et la méthode <xref:System.Windows.Forms.Control.BeginInvoke%2A> pour rechercher des fichiers de façon asynchrone.  
  
## <a name="reference"></a>Référence  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documente un composant qui encapsule un thread de travail pour les opérations asynchrones.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Explique comment charger un son de façon asynchrone.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Décrit comment charger une image de manière asynchrone.  
  
## <a name="related-sections"></a>Sections connexes  
 [Guide pratique pour exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md)  
 Montre comment effectuer une opération qui prend du temps avec le composant <xref:System.ComponentModel.BackgroundWorker>.  
  
 [Vue d'ensemble du composant BackgroundWorker](backgroundworker-component-overview.md)  
 Fournit des rubriques qui décrivent comment utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour les opérations asynchrones.
