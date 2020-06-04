---
title: Définition de classes
ms.date: 07/20/2015
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
ms.openlocfilehash: 646c6ce307131f3edba194af19920eade9c1753c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389112"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Procédure pas à pas : définition des classes (Visual Basic)

Cette procédure pas à pas montre comment définir des classes, que vous pouvez ensuite utiliser pour créer des objets. Elle vous montre également comment ajouter des propriétés et des méthodes à la nouvelle classe, et montre comment initialiser un objet.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Pour définir une classe
  
1. Créez un projet en cliquant sur **nouveau projet** dans le menu **fichier** . La boîte de dialogue **Nouveau projet** apparaît.  
  
2. Sélectionnez application Windows dans la liste des modèles de projet de Visual Basic pour afficher le nouveau projet.  
  
3. Ajoutez une nouvelle classe au projet en cliquant sur **Ajouter une classe** dans le menu **projet** . La boîte de dialogue **Ajouter un nouvel élément** s'affiche.  
  
4. Sélectionnez le modèle de **classe** .  
  
5. Nommez la nouvelle classe `UserNameInfo.vb` , puis cliquez sur **Ajouter** pour afficher le code de la nouvelle classe.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Vous pouvez utiliser l' **éditeur de Code** Visual Basic pour ajouter une classe à votre formulaire de démarrage en tapant le `Class` mot clé suivi du nom de la nouvelle classe. L' **éditeur de code** fournit une `End Class` instruction correspondante.  
  
6. Définissez un champ privé pour la classe en ajoutant le code suivant entre les `Class` `End Class` instructions et :  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     La déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe. Vous pouvez rendre les champs disponibles à l’extérieur d’une classe en utilisant des modificateurs d’accès tels que `Public` qui fournissent plus d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../declared-elements/access-levels.md).  
  
7. Définissez une propriété pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Définissez une méthode pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Définissez un constructeur paramétrable pour la nouvelle classe en ajoutant une procédure nommée `Sub New` :  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     Le `Sub New` constructeur est appelé automatiquement lorsqu’un objet basé sur cette classe est créé. Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Pour créer un bouton pour tester la classe
  
1. Modifiez le formulaire de démarrage en mode Design en cliquant avec le bouton droit sur son nom dans **Explorateur de solutions** puis en cliquant sur **Concepteur de vues**. Par défaut, le formulaire de démarrage pour les projets d’application Windows est nommé Form1. vb. Le formulaire principal s’affiche alors.  
  
2. Ajoutez un bouton au formulaire principal et double-cliquez dessus pour afficher le code du gestionnaire d' `Button1_Click` événements. Ajoutez le code suivant pour appeler la procédure de test :  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Pour exécuter votre application
  
1. Exécutez votre application en appuyant sur F5. Cliquez sur le bouton du formulaire pour appeler la procédure de test. Il affiche un message indiquant que l’original `UserName` est « Moore, Bobby », parce que la procédure a appelé la `Capitalize` méthode de l’objet.  
  
2. Cliquez sur **OK** pour fermer la boîte de message. La `Button1 Click` procédure modifie la valeur de la `UserName` propriété et affiche un message indiquant que la nouvelle valeur de `UserName` est « worden, Joe ».  
  
## <a name="see-also"></a>Voir aussi

- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Objets et classes](index.md)
