---
title: 'Procédure : appliquer le modèle PropertyNameChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- data binding [Windows Forms], custom controls
- PropertyNameChanged pattern [Windows Forms], applying
ms.assetid: aa47ddf6-5223-40c4-833f-a78992194836
ms.openlocfilehash: 01afa713e97206ea192ba55dc2affad20163f872
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665263"
---
# <a name="how-to-apply-the-propertynamechanged-pattern"></a>Procédure : appliquer le modèle PropertyNameChanged
L’exemple de code suivant montre comment appliquer le *PropertyName*modèle a été modifié pour un contrôle personnalisé. Appliquer ce modèle lorsque vous implémentez des contrôles personnalisés qui sont utilisés avec le moteur de liaison de données Windows Forms.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/CS/Form1.cs#3)]
 [!code-vb[System.Windows.Forms.ChangeNotification#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ChangeNotification/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler l’exemple de code précédent :  
  
- Collez le code dans un fichier de code vide. Vous devez utiliser le contrôle personnalisé dans un formulaire Windows qui contient un `Main` (méthode).  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Implémenter l’Interface INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md)
- [Notification de modifications dans la liaison de données Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
