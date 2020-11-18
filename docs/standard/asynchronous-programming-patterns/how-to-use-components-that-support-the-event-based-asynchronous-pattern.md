---
title: 'Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 94bd79bab1e7982ea39b5aa5872a6674033f9ccf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830361"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Procédure : utiliser des composants qui prennent en charge le modèle asynchrone basé sur des événements
De nombreux composants peuvent effectuer leur travail de façon asynchrone. Les composants <xref:System.Media.SoundPlayer> et <xref:System.Windows.Forms.PictureBox>, par exemple, permettent de charger des sons et des images « en arrière-plan » pendant que le thread principal continue de s’exécuter sans interruption.  
  
 Il peut être aussi simple d’utiliser des méthodes asynchrones sur une classe qui prend en charge la [Vue d’ensemble du modèle asynchrone basé sur les événements](event-based-asynchronous-pattern-overview.md) que d’attacher un gestionnaire d’événements à l’événement _MethodName_**Completed**, comme pour n’importe quel autre événement. Lorsque vous appelez la méthode _MethodName_**Async**, votre application continuera de s’exécuter sans interruption jusqu'à ce que l’événement _MethodName_**Completed** soit déclenché. Dans votre gestionnaire d’événements, vous pouvez examiner le paramètre <xref:System.ComponentModel.AsyncCompletedEventArgs> pour déterminer si l’opération asynchrone s’est terminée avec succès ou si elle a été annulée.  
  
 Pour plus d’informations sur les gestionnaires d’événements, consultez la page [Vue d’ensemble des gestionnaires d’événements](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).  
  
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

- [Procédure : exécuter une opération en arrière-plan](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [Vue d’ensemble du modèle asynchrone basé sur des événements](event-based-asynchronous-pattern-overview.md)
