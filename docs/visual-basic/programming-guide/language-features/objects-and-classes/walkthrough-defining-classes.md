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
ms.openlocfilehash: bd3f6e5cff41551240d9904ab93af8758eb104d2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346076"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Procédure pas à pas : définition des classes (Visual Basic)

Cette procédure pas à pas montre comment définir des classes, que vous pouvez ensuite utiliser pour créer des objets. Elle vous montre également comment ajouter des propriétés et des méthodes à la nouvelle classe, et montre comment initialiser un objet.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Pour définir une classe
  
1. Créez un projet en cliquant sur **nouveau projet** dans le menu **fichier** . La boîte de dialogue **Nouveau projet** s'affiche.  
  
2. Sélectionnez application Windows dans la liste des modèles de projet de Visual Basic pour afficher le nouveau projet.  
  
3. Ajoutez une nouvelle classe au projet en cliquant sur **Ajouter une classe** dans le menu **projet** . La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
4. Sélectionnez le modèle de **classe** .  
  
5. Nommez la nouvelle classe `UserNameInfo.vb`, puis cliquez sur **Ajouter** pour afficher le code de la nouvelle classe.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Vous pouvez utiliser l' **éditeur de Code** Visual Basic pour ajouter une classe à votre formulaire de démarrage en tapant le mot clé `Class` suivi du nom de la nouvelle classe. L' **éditeur de code** fournit une instruction `End Class` correspondante.  
  
6. Définissez un champ privé pour la classe en ajoutant le code suivant entre les instructions `Class` et `End Class` :  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     La déclaration du champ comme `Private` signifie qu’il peut être utilisé uniquement dans la classe. Vous pouvez rendre les champs disponibles à l’extérieur d’une classe en utilisant des modificateurs d’accès tels que `Public` qui fournissent plus d’accès. Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Définissez une propriété pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Définissez une méthode pour la classe en ajoutant le code suivant :  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Définissez un constructeur paramétrable pour la nouvelle classe en ajoutant une procédure nommée `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     Le constructeur `Sub New` est appelé automatiquement lorsqu’un objet basé sur cette classe est créé. Ce constructeur définit la valeur du champ qui contient le nom d’utilisateur.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Pour créer un bouton pour tester la classe
  
1. Modifiez le formulaire de démarrage en mode Design en cliquant avec le bouton droit sur son nom dans **Explorateur de solutions** puis en cliquant sur **Concepteur de vues**. Par défaut, le formulaire de démarrage pour les projets d’application Windows est nommé Form1. vb. Le formulaire principal s’affiche alors.  
  
2. Ajoutez un bouton au formulaire principal et double-cliquez dessus pour afficher le code du gestionnaire d’événements `Button1_Click`. Ajoutez le code suivant pour appeler la procédure de test :  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Pour exécuter votre application
  
1. Exécutez votre application en appuyant sur F5. Cliquez sur le bouton du formulaire pour appeler la procédure de test. Il affiche un message indiquant que la `UserName` d’origine est « MOORE, BOBBY », car la procédure a appelé la méthode `Capitalize` de l’objet.  
  
2. Cliquez sur **OK** pour fermer la boîte de message. La procédure `Button1 Click` modifie la valeur de la propriété `UserName` et affiche un message indiquant que la nouvelle valeur de `UserName` est « worden, Joe ».  
  
## <a name="see-also"></a>Voir aussi

- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
