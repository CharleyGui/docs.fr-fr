---
title: Multithreading dans les contrôles Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- BackgroundWorker component
- threading [Windows Forms], controls
ms.assetid: c311d652-0f26-45fa-bdcc-b1615d73ce4e
ms.openlocfilehash: cf6790172b7445ad154eead5d17f8efddd78ffee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952684"
---
# <a name="multithreading-in-windows-forms-controls"></a>Multithreading dans les contrôles Windows Forms
Dans de nombreuses applications, vous pouvez rendre votre interface utilisateur plus réactive en effectuant des opérations qui prennent du temps sur un autre thread. Un certain nombre d’outils sont disponibles pour le multithreading de vos contrôles de <xref:System.Threading> Windows Forms, y <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> compris l’espace de `BackgroundWorker` noms, la méthode et le composant.  
  
> [!NOTE]
> Le `BackgroundWorker` composant remplace et ajoute des fonctionnalités à <xref:System.Threading> l’espace de <xref:System.Windows.Forms.Control.BeginInvoke%2A?displayProperty=nameWithType> noms et à la méthode; Toutefois, celles-ci sont conservées pour la compatibilité descendante et l’utilisation ultérieure, si vous le souhaitez. Pour plus d’informations, consultez [vue d’ensemble du composant BackgroundWorker](backgroundworker-component-overview.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Effectuer des appels thread-safe à des contrôles Windows Forms](how-to-make-thread-safe-calls-to-windows-forms-controls.md)  
 Montre comment effectuer des appels thread-safe pour Windows Forms contrôles.  
  
 [Guide pratique pour Utiliser un thread d’arrière-plan pour rechercher des fichiers](how-to-use-a-background-thread-to-search-for-files.md)  
 Montre comment utiliser l' <xref:System.Threading> espace de noms et la <xref:System.Windows.Forms.Control.BeginInvoke%2A> méthode pour rechercher des fichiers de façon asynchrone.  
  
## <a name="reference"></a>Référence  
 <xref:System.ComponentModel.BackgroundWorker>  
 Documente un composant qui encapsule un thread de travail pour les opérations asynchrones.  
  
 <xref:System.Media.SoundPlayer.LoadAsync%2A>  
 Explique comment charger un son de façon asynchrone.  
  
 <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>  
 Décrit comment charger une image de manière asynchrone.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Guide pratique pour exécuter une opération en arrière-plan](how-to-run-an-operation-in-the-background.md)  
 Montre comment effectuer une opération qui prend du temps avec le <xref:System.ComponentModel.BackgroundWorker> composant.  
  
 [Vue d'ensemble du composant BackgroundWorker](backgroundworker-component-overview.md)  
 Fournit des rubriques qui décrivent comment utiliser <xref:System.ComponentModel.BackgroundWorker> le composant pour les opérations asynchrones.
