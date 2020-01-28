---
title: Créer une application Windows Forms à partir de la ligne de commande
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: da6b9da53a36a44233dde4f0d1c4f147d913c7cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739522"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Comment : créer une application Windows Forms à partir de la ligne de commande

Les procédures suivantes décrivent les étapes de base que vous devez effectuer pour créer et exécuter une application Windows Forms à partir de la ligne de commande. Ces procédures sont très bien prises en charge dans Visual Studio.  Consultez également [procédure pas à pas : Hébergement d’un contrôle de Windows Forms dans WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-create-the-form"></a>Pour créer le formulaire  
  
1. Dans un fichier de code vide, tapez les instructions `Imports` ou `using` suivantes :  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Déclarez une classe nommée `Form1` qui hérite de la classe Form :
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Créez un constructeur sans paramètre pour `Form1`.
  
     Vous ajouterez du code au constructeur lors d'une procédure ultérieure.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Ajoutez une méthode `Main` à la classe.
  
    1. Appliquez la <xref:System.STAThreadAttribute> à la C# méthode `Main` pour spécifier que votre application Windows Forms est un cloisonnement à thread unique. (L’attribut n’est pas nécessaire dans Visual Basic, puisque les applications Windows Forms développées avec Visual Basic utilisent un modèle à thread unique cloisonné par défaut.)  
  
    2. Appelez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pour appliquer des styles de système d’exploitation à votre application.  
  
    3. Créez une instance du formulaire et exécutez-la.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Pour compiler et exécuter l'application  
  
1. À l'invite de commandes .NET Framework, accédez au répertoire où vous avez créé la classe `Form1`.  
  
2. Compilez le formulaire.  
  
    - Si vous utilisez C#, tapez : `csc form1.cs`  
  
         `-or-`  
  
    - Si vous utilisez Visual Basic, tapez : `vbc form1.vb`  
  
3. À l’invite de commandes, tapez : `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Ajout d’un contrôle et gestion d’un événement

Les étapes de la procédure précédente illustrent simplement comment créer un Windows Form de base qui se compile et s'exécute. La procédure suivante illustre comment créer et ajouter un contrôle au formulaire et comment gérer un événement pour le contrôle. Pour plus d’informations sur les contrôles que vous pouvez ajouter à Windows Forms, consultez [Windows Forms contrôles](./controls/index.md).
  
 Outre la création d’applications Windows Forms, vous devez comprendre la programmation basée sur les événements et comment gérer l’entrée d’utilisateur. Pour plus d’informations, consultez [création de gestionnaires d’événements dans Windows Forms](creating-event-handlers-in-windows-forms.md)et [gestion des entrées d’utilisateur](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Pour déclarer un contrôle bouton et gérer son événement click  
  
1. Déclarez un contrôle bouton nommé `button1`.  
  
2. Dans le constructeur, créez le bouton et définissez ses propriétés <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Text%2A>.  
  
3. Ajoutez le bouton au formulaire.  
  
     L’exemple de code suivant montre comment déclarer le contrôle Button :
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Créez une méthode pour gérer l'événement <xref:System.Windows.Forms.Control.Click> pour le bouton.  
  
5. Dans le gestionnaire d'événements click, affichez un <xref:System.Windows.Forms.MessageBox> avec le message « Hello World ».  
  
     L’exemple de code suivant montre comment gérer l’événement Click du contrôle Button :
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Associez l'événement <xref:System.Windows.Forms.Control.Click> à la méthode que vous avez créée.  
  
     L'exemple de code suivant montre comment associer l'événement à la méthode.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Compilez et exécutez l'application comme décrit dans la procédure précédente.  
  
## <a name="example"></a>Exemple  
 
L’exemple de code suivant est l’exemple complet des procédures précédentes :
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Modification de l'apparence des Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Amélioration des applications Windows Forms](./advanced/index.md)
- [Bien démarrer avec Windows Forms](getting-started-with-windows-forms.md)
