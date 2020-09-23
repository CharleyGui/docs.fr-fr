---
title: Propriétés implémentées automatiquement
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: f50b1f40ef9843391c6622561bfd8a8eaae6fc17
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090052"
---
# <a name="auto-implemented-properties-visual-basic"></a>Propriétés implémentées automatiquement (Visual Basic)

Les *Propriétés implémentées automatiquement* vous permettent de spécifier rapidement une propriété d’une classe sans avoir à écrire du code dans `Get` et à `Set` la propriété. Quand vous écrivez du code pour une propriété implémentée automatiquement, le compilateur Visual Basic crée automatiquement un champ privé pour stocker la variable de propriété en plus de créer les procédures `Get` et `Set` associées.  
  
 Avec les propriétés implémentées automatiquement, une propriété, y compris une valeur par défaut, peut être déclarée en une seule ligne. L'exemple suivant montre trois déclarations de propriété.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Une propriété implémentée automatiquement est équivalente à une propriété dont la valeur de propriété est stockée dans un champ privé. L'exemple de code suivant montre une propriété implémentée automatiquement.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 L'exemple de code suivant montre le code équivalent pour l'exemple précédent de propriété implémentée automatiquement.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Le code suivant montre l'implémentation des propriétés en lecture seule :  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 Vous pouvez assigner la propriété avec des expressions d'initialisation, comme illustré dans cet exemple, ou vous pouvez assigner les propriétés dans le constructeur du type conteneur.  Vous pouvez assigner les champs de stockage des propriétés en lecture seule à tout moment.  
  
## <a name="backing-field"></a>Champ de stockage  

 Quand vous déclarez une propriété implémentée automatiquement, Visual Basic crée automatiquement un champ privé masqué appelé *champ de stockage* pour contenir la valeur de la propriété. Le nom du champ de stockage correspond au nom de la propriété implémentée automatiquement précédé d'un trait de soulignement (_). Par exemple, si vous déclarez une propriété implémentée automatiquement nommée `ID`, le champ de stockage est nommé `_ID`. Si vous incluez un membre de votre classe également nommé `_ID`, vous créez un conflit de noms et Visual Basic signale une erreur du compilateur.  
  
 Le champ de stockage possède également les caractéristiques suivantes :  
  
- Le modificateur d'accès pour le champ de stockage est toujours `Private`, même quand la propriété a elle-même un niveau d'accès différent, tel que `Public`.  
  
- Si la propriété est marquée comme `Shared`, le champ de stockage est également partagé.  
  
- Les attributs spécifiés pour la propriété ne s'appliquent pas au champ de stockage.  
  
- Le champ de stockage est accessible à partir du code dans la classe et des outils de débogage tels que la fenêtre Espion. Toutefois, le champ de stockage ne s'affiche pas dans une liste de saisie semi-automatique IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Initialisation d'une propriété implémentée automatiquement  

 Toute expression pouvant être utilisée pour initialiser un champ est valide pour l'initialisation d'une propriété implémentée automatiquement. Quand vous initialisez une propriété implémentée automatiquement, l'expression est évaluée et passée à la procédure `Set` pour la propriété. Les exemples de code suivants montrent certaines propriétés implémentées automatiquement qui incluent des valeurs initiales.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Vous ne pouvez pas initialiser une propriété implémentée automatiquement qui est membre d'une `Interface` ou qui est marquée `MustOverride`.  
  
 Quand vous déclarez une propriété implémentée automatiquement en tant que membre d'une `Structure`, vous pouvez initialiser la propriété implémentée automatiquement seulement si elle est marquée `Shared`.  
  
 Quand vous déclarez une propriété implémentée automatiquement en tant que tableau, vous ne pouvez pas spécifier des limites d'index de tableau explicites. Toutefois, vous pouvez fournir une valeur à l'aide d'un initialiseur de tableau, comme indiqué dans les exemples suivants.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Définitions de propriétés qui requièrent la syntaxe standard  

 Les propriétés implémentées automatiquement sont pratiques et prennent en charge de nombreux scénarios de programmation. Toutefois, il existe des situations où vous ne pouvez pas utiliser une propriété implémentée automatiquement et que vous devez utiliser la syntaxe de propriété standard, ou *développée*.  
  
 Vous devez utiliser la syntaxe de définition de propriété développée pour effectuer les opérations suivantes :  
  
- Ajouter du code à la procédure `Get` ou `Set` d'une propriété, tel que du code permettant de valider des valeurs entrantes dans la procédure `Set`. Par exemple, vous pouvez vérifier qu'une chaîne représentant un numéro de téléphone contient le nombre de chiffres requis avant de définir la valeur de la propriété.  
  
- Spécifier une accessibilité différente pour les procédures `Get` et `Set`. Par exemple, vous souhaiterez peut-être définir la procédure `Set` comme `Private` et la procédure `Get` comme `Public`.  
  
- Créer des propriétés `WriteOnly`.  
  
- Utiliser des propriétés paramétrables (notamment les propriétés `Default`). Vous devez déclarer une propriété développée pour pouvoir spécifier un paramètre pour la propriété, ou pour spécifier des paramètres supplémentaires pour la procédure `Set`.  
  
- Placer un attribut sur le champ de stockage ou modifier le niveau d'accès du champ de stockage.  
  
- Fournir des commentaires XML pour le champ de stockage.  
  
## <a name="expanding-an-auto-implemented-property"></a>Développement d’une propriété implémentée automatiquement  

 Si vous devez convertir une propriété implémentée automatiquement en une propriété développée qui contient une procédure `Get` ou `Set`, l’éditeur de code de Visual Basic peut générer automatiquement les procédures `Get` et `Set`, et l’instruction `End Property` pour la propriété. Le code est généré si vous placez le curseur sur une ligne vide après l' `Property` instruction, que vous tapez un `G` (pour `Get` ) ou un `S` (pour `Set` ) et que vous appuyez sur entrée. L'éditeur de code de Visual Basic génère automatiquement la procédure `Get` ou `Set` pour les propriétés en lecture seule et en écriture seule quand vous appuyez sur Entrée à la fin d'une instruction `Property`.  
  
## <a name="see-also"></a>Voir aussi

- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property Statement](../../../language-reference/statements/property-statement.md)
- [Lecture seule](../../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Objets et classes](../objects-and-classes/index.md)
