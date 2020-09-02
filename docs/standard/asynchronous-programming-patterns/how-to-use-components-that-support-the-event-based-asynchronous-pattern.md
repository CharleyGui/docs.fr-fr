---
title: 'Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: e23a9b28cff9428cbc8896515ce71db85c832243
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379146"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements
De nombreux composants peuvent effectuer leur travail de façon asynchrone. Les composants <xref:System.Media.SoundPlayer> et <xref:System.Windows.Forms.PictureBox>, par exemple, permettent de charger des sons et des images « en arrière-plan » pendant que le thread principal continue de s’exécuter sans interruption.  
  
 Il peut être aussi simple d’utiliser des méthodes asynchrones sur une classe qui prend en charge la [Vue d’ensemble du modèle asynchrone basé sur les événements](event-based-asynchronous-pattern-overview.md) que d’attacher un gestionnaire d’événements à l’événement _MethodName_**Completed**, comme pour n’importe quel autre événement. Lorsque vous appelez la méthode _MethodName_**Async**, votre application continuera de s’exécuter sans interruption jusqu'à ce que l’événement _MethodName_**Completed** soit déclenché. Dans votre gestionnaire d’événements, vous pouvez examiner le paramètre <xref:System.ComponentModel.AsyncCompletedEventArgs> pour déterminer si l’opération asynchrone s’est terminée avec succès ou si elle a été annulée.  
  
 Pour plus d’informations sur les gestionnaires d’événements, consultez la page [Vue d’ensemble des gestionnaires d’événements](../../framework/winforms/event-handlers-overview-windows-forms.md).  
  
 La procédure suivante montre comment utiliser la fonction de chargement d’image asynchrone d’un contrôle <xref:System.Windows.Forms.PictureBox>.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Autoriser un contrôle PictureBox à charger une image de façon asynchrone  
  
1. Créez une instance du composant <xref:System.Windows.Forms.PictureBox> dans votre formulaire.  
  
2. Affectez un gestionnaire d'événements à l'événement <xref:System.Windows.Forms.PictureBox.LoadCompleted>.  
  
     Regardez si des erreurs s’y sont produites pendant le téléchargement asynchrone. C’est également ici qu’il faut vérifier si une annulation est survenue.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. Ajoutez deux boutons, nommés `loadButton` et `cancelLoadButton`, à votre formulaire. Ajoutez des gestionnaires d’événements <xref:System.Windows.Forms.Control.Click> pour démarrer et annuler le téléchargement.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. Exécutez votre application.  
  
     Pendant le téléchargement de l’image, vous pourrez déplacer librement le formulaire, le réduire et l’agrandir.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : exécuter une opération en arrière-plan](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
