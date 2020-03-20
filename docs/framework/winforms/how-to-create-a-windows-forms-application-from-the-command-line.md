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
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181986"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Comment : Créer une application Windows Forms à partir de la ligne de commande

Les procédures suivantes décrivent les étapes de base que vous devez effectuer pour créer et exécuter une application Windows Forms à partir de la ligne de commande. Ces procédures sont très bien prises en charge dans Visual Studio.  Voir aussi [Pas à pas : Héberger un contrôle des formulaires Windows dans WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Procédure  
  
#### <a name="to-create-the-form"></a>Pour créer le formulaire  
  
1. Dans un fichier de code `Imports` `using` vide, tapez les éléments suivants ou les relevés :  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Déclarez une `Form1` classe nommée qui hérite de la classe de formulaire :
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Créez un constructeur sans `Form1`paramètres pour .
  
     Vous ajouterez du code au constructeur lors d'une procédure ultérieure.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Ajoutez une méthode `Main` à la classe.
  
    1. Appliquez <xref:System.STAThreadAttribute> la méthode `Main` C pour spécifier votre application Windows Forms est un appartement à threads unique. (L’attribut n’est pas nécessaire dans Visual Basic, puisque Windows forme des applications développées avec Visual Basic utiliser un modèle d’appartement à threads unique par défaut.)  
  
    2. Appelez <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> pour appliquer des styles de système d’exploitation à votre application.  
  
    3. Créez une instance du formulaire et exécutez-la.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Pour compiler et exécuter l'application  
  
1. À l'invite de commandes .NET Framework, accédez au répertoire où vous avez créé la classe `Form1`.  
  
2. Compilez le formulaire.  
  
    - Si vous utilisez le C, tapez :`csc form1.cs`  
  
         `-or-`  
  
    - Si vous utilisez Visual Basic, tapez :`vbc form1.vb`  
  
3. À l’invite de commandes, tapez : `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Ajout d’un contrôle et gestion d’un événement

Les étapes de la procédure précédente illustrent simplement comment créer un Windows Form de base qui se compile et s'exécute. La procédure suivante illustre comment créer et ajouter un contrôle au formulaire et comment gérer un événement pour le contrôle. Pour plus d’informations sur les contrôles que vous pouvez ajouter aux formulaires Windows, voir [Windows Forms Controls](./controls/index.md).
  
 Outre la création d’applications Windows Forms, vous devez comprendre la programmation basée sur les événements et comment gérer l’entrée d’utilisateur. Pour plus d’informations, voir [Créer des gestionnaires d’événements dans les formulaires Windows](creating-event-handlers-in-windows-forms.md)et traiter [l’entrée des utilisateurs](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Pour déclarer un contrôle bouton et gérer son événement click  
  
1. Déclarez un contrôle bouton nommé `button1`.  
  
2. Dans le constructeur, créez le bouton et définissez ses propriétés <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> et <xref:System.Windows.Forms.Control.Text%2A>.  
  
3. Ajoutez le bouton au formulaire.  
  
     L’exemple de code suivant montre comment déclarer le contrôle du bouton :
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Créez une méthode pour gérer l'événement <xref:System.Windows.Forms.Control.Click> pour le bouton.  
  
5. Dans le gestionnaire d'événements click, affichez un <xref:System.Windows.Forms.MessageBox> avec le message « Hello World ».  
  
     L’exemple de code suivant montre comment gérer l’événement de clic du contrôle des boutons :
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Associez l'événement <xref:System.Windows.Forms.Control.Click> à la méthode que vous avez créée.  
  
     L'exemple de code suivant montre comment associer l'événement à la méthode.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Compilez et exécutez l'application comme décrit dans la procédure précédente.  
  
## <a name="example"></a> Exemple  

L’exemple de code suivant est l’exemple complet des procédures précédentes :
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Modification de l'apparence des Windows Forms](changing-the-appearance-of-windows-forms.md)
- [Amélioration des applications Windows Forms](./advanced/index.md)
- [Bien démarrer avec Windows Forms](getting-started-with-windows-forms.md)
