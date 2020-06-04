---
title: Création et implémentation d’interfaces
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 89e8f91a04b25b84bc783d5c4f4b91cf12426f72
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405065"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Procédure pas à pas : création et implémentation d'interfaces (Visual Basic)

Les interfaces décrivent les caractéristiques des propriétés, des méthodes et des événements, mais laissent les détails de l’implémentation à des structures ou des classes.  
  
 Cette procédure pas à pas montre comment déclarer et implémenter une interface.  
  
> [!NOTE]
> Cette procédure pas à pas ne fournit pas d’informations sur la création d’une interface utilisateur.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Pour définir une interface
  
1. Ouvrez un nouveau projet d’application Windows Visual Basic.  
  
2. Ajoutez un nouveau module au projet en cliquant sur **Ajouter un module** dans le menu **projet** .  
  
3. Nommez le nouveau module `Module1.vb` , puis cliquez sur **Ajouter**. Le code du nouveau module s’affiche.  
  
4. Définissez une interface nommée `TestInterface` dans `Module1` en tapant `Interface TestInterface` entre les `Module` `End Module` instructions et, puis en appuyant sur entrée. L' **éditeur de code** met en retrait le `Interface` mot clé et ajoute une `End Interface` instruction pour former un bloc de code.  
  
5. Définissez une propriété, une méthode et un événement pour l’interface en plaçant le code suivant entre `Interface` les `End Interface` instructions et :  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implémentation

 Vous pouvez remarquer que la syntaxe utilisée pour déclarer des membres d’interface est différente de la syntaxe utilisée pour déclarer des membres de classe. Cette différence reflète le fait que les interfaces ne peuvent pas contenir de code d’implémentation.  
  
### <a name="to-implement-the-interface"></a>Pour implémenter l’interface
  
1. Ajoutez une classe nommée `ImplementationClass` en ajoutant l’instruction suivante à `Module1` , après l' `End Interface` instruction mais avant l' `End Module` instruction, puis en appuyant sur entrée :  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** fournit une `End Class` instruction correspondante lorsque vous appuyez sur entrée.  
  
2. Ajoutez l' `Implements` instruction suivante à `ImplementationClass` , qui nomme l’interface que la classe implémente :  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     En cas de liste distincte des autres éléments en haut d’une classe ou d’une structure, l' `Implements` instruction indique que la classe ou la structure implémente une interface.  
  
     Si vous travaillez dans l’environnement de développement intégré, l' **éditeur de code** implémente les membres de classe requis par `TestInterface` lorsque vous appuyez sur entrée, et vous pouvez ignorer l’étape suivante.  
  
3. Si vous ne travaillez pas dans l’environnement de développement intégré, vous devez implémenter tous les membres de l’interface `MyInterface` . Ajoutez le code suivant à `ImplementationClass` pour implémenter `Event1` , `Method1` et `Prop1` :  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     L' `Implements` instruction nomme l’interface et le membre d’interface en cours d’implémentation.  
  
4. Terminez la définition de `Prop1` en ajoutant un champ privé à la classe qui a stocké la valeur de la propriété :  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Retourne la valeur de `pval` à partir de l’accesseur Get de la propriété.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Définissez la valeur de `pval` dans l’accesseur Set de propriété.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Terminez la définition de `Method1` en ajoutant le code suivant.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Pour tester l’implémentation de l’interface
  
1. Cliquez avec le bouton droit sur le formulaire de démarrage de votre projet dans la **Explorateur de solutions**, puis cliquez sur **afficher le code**. L’éditeur affiche la classe pour votre formulaire de démarrage. Par défaut, le formulaire de démarrage est appelé `Form1` .  
  
2. Ajoutez le `testInstance` champ suivant à la `Form1` classe :  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     En déclarant `testInstance` en tant que `WithEvents` , la `Form1` classe peut gérer ses événements.  
  
3. Ajoutez le gestionnaire d’événements suivant à la `Form1` classe pour gérer les événements déclenchés par `testInstance` :  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Ajoutez une sous-routine nommée `Test` à la `Form1` classe pour tester la classe d’implémentation :  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     La `Test` procédure crée une instance de la classe qui implémente `MyInterface` , assigne cette instance au `testInstance` champ, définit une propriété et exécute une méthode par le biais de l’interface.  
  
5. Ajoutez du code pour appeler la `Test` procédure à partir de la `Form1 Load` procédure de votre formulaire de démarrage :  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Exécutez la `Test` procédure en appuyant sur F5. Le message « Prop1 a été défini sur 9 » s’affiche. Une fois que vous avez cliqué sur OK, le message « le paramètre X pour méthode1 est 5 » s’affiche. Cliquez sur OK. le message « le gestionnaire d’événements a intercepté l’événement » s’affiche.  
  
## <a name="see-also"></a>Voir aussi

- [Implements, instruction](../../../language-reference/statements/implements-statement.md)
- [Interfaces](index.md)
- [Interface (instruction)](../../../language-reference/statements/interface-statement.md)
- [Event, instruction](../../../language-reference/statements/event-statement.md)
