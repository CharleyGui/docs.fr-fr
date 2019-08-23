---
title: Création et implémentation d’interfaces (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923318"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Procédure pas à pas : Création et implémentation d’interfaces (Visual Basic)

Les interfaces décrivent les caractéristiques des propriétés, des méthodes et des événements, mais laissent les détails de l’implémentation à des structures ou des classes.  
  
 Cette procédure pas à pas montre comment déclarer et implémenter une interface.  
  
> [!NOTE]
> Cette procédure pas à pas ne fournit pas d’informations sur la création d’une interface utilisateur.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Pour définir une interface
  
1. Ouvrez un nouveau projet d’application Windows Visual Basic.  
  
2. Ajoutez un nouveau module au projet en cliquant sur **Ajouter un module** dans le menu **projet** .  
  
3. Nommez le nouveau `Module1.vb` module, puis cliquez sur **Ajouter**. Le code du nouveau module s’affiche.  
  
4. Définissez une interface nommée `TestInterface` dans `Module1` en tapant `Interface TestInterface` entre les `Module` instructions `End Module` et, puis en appuyant sur entrée. L' **éditeur de code** met en `Interface` retrait le mot clé `End Interface` et ajoute une instruction pour former un bloc de code.  
  
5. Définissez une propriété, une méthode et un événement pour l’interface en plaçant le code suivant entre `Interface` les `End Interface` instructions et:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implémentation

 Vous pouvez remarquer que la syntaxe utilisée pour déclarer des membres d’interface est différente de la syntaxe utilisée pour déclarer des membres de classe. Cette différence reflète le fait que les interfaces ne peuvent pas contenir de code d’implémentation.  
  
### <a name="to-implement-the-interface"></a>Pour implémenter l’interface
  
1. Ajoutez une classe nommée `ImplementationClass` en ajoutant l’instruction suivante à `Module1`, après l' `End Interface` instruction mais avant l' `End Module` instruction, puis en appuyant sur entrée:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** fournit une `End Class` instruction correspondante lorsque vous appuyez sur entrée.  
  
2. Ajoutez l’instruction `Implements` suivante à `ImplementationClass`, qui nomme l’interface que la classe implémente:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     En cas de liste distincte des autres éléments en haut d’une classe ou d’une `Implements` structure, l’instruction indique que la classe ou la structure implémente une interface.  
  
     Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** implémente les membres de classe `TestInterface` requis par lorsque vous appuyez sur entrée, et vous pouvez ignorer l’étape suivante.  
  
3. Si vous ne travaillez pas dans l’environnement de développement intégré, vous devez implémenter tous les membres de `MyInterface`l’interface. Ajoutez le code suivant à `ImplementationClass` pour implémenter `Method1` `Event1`, et `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     L' `Implements` instruction nomme l’interface et le membre d’interface en cours d’implémentation.  
  
4. Terminez la définition `Prop1` de en ajoutant un champ privé à la classe qui a stocké la valeur de la propriété:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Retourne la valeur de `pval` à partir de l’accesseur Get de la propriété.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Définissez la valeur de `pval` dans l’accesseur Set de propriété.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Terminez la définition `Method1` de en ajoutant le code suivant.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Pour tester l’implémentation de l’interface
  
1. Cliquez avec le bouton droit sur le formulaire de démarrage de votre projet dans la **Explorateur de solutions**, puis cliquez sur **afficher le code**. L’éditeur affiche la classe pour votre formulaire de démarrage. Par défaut, le formulaire de démarrage est `Form1`appelé.  
  
2. Ajoutez le champ `testInstance` suivant à la `Form1` classe:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     En déclarant `testInstance` en tant `WithEvents`que, `Form1` la classe peut gérer ses événements.  
  
3. Ajoutez le gestionnaire d’événements suivant à `Form1` la classe pour gérer les événements `testInstance`déclenchés par:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Ajoutez une sous-routine `Test` nommée à `Form1` la classe pour tester la classe d’implémentation:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     La `Test` procédure crée une instance de la classe qui `MyInterface`implémente, assigne cette instance au `testInstance` champ, définit une propriété et exécute une méthode par le biais de l’interface.  
  
5. Ajoutez du code pour appeler `Test` la procédure à `Form1 Load` partir de la procédure de votre formulaire de démarrage:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Exécutez la `Test` procédure en appuyant sur F5. Le message «Prop1 a été défini sur 9» s’affiche. Une fois que vous avez cliqué sur OK, le message «le paramètre X pour méthode1 est 5» s’affiche. Cliquez sur OK. le message «le gestionnaire d’événements a intercepté l’événement» s’affiche.  
  
## <a name="see-also"></a>Voir aussi

- [Implements (instruction)](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfaces](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Interface (instruction)](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event (instruction)](../../../../visual-basic/language-reference/statements/event-statement.md)
