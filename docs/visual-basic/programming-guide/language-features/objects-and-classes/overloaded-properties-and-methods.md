---
title: Propriétés et méthodes surchargées
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346090"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Propriétés et méthodes surchargées (Visual Basic)

La surcharge est la création de plusieurs procédures, constructeur d’instance ou propriété dans une classe portant le même nom mais avec des types d’arguments différents.

## <a name="overloading-usage"></a>Surcharge de l’utilisation

La surcharge est particulièrement utile lorsque votre modèle objet impose que vous utilisiez des noms identiques pour les procédures qui opèrent sur des types de données différents. Par exemple, une classe qui peut afficher plusieurs types de données différents peut avoir `Display` procédures qui ressemblent à ceci :

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Sans surcharge, vous devez créer des noms distincts pour chaque procédure, même s’ils font la même chose, comme indiqué ci-dessous :

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

La surcharge facilite l’utilisation des propriétés ou des méthodes, car elle permet de choisir les types de données qui peuvent être utilisés. Par exemple, la méthode surchargée `Display` présentée précédemment peut être appelée avec l’une des lignes de code suivantes :

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

Au moment de l’exécution, Visual Basic appelle la procédure appropriée en fonction des types de données des paramètres que vous spécifiez.

## <a name="overloading-rules"></a>Surcharge des règles

 Pour créer un membre surchargé pour une classe, vous devez ajouter au moins deux propriétés ou méthodes portant le même nom. À l’exception des membres dérivés surchargés, chaque membre surchargé doit avoir des listes de paramètres différentes, et les éléments suivants ne peuvent pas être utilisés en tant que fonctionnalité de différenciation lors de la surcharge d’une propriété ou d’une procédure :

- Les modificateurs, tels que `ByVal` ou `ByRef`, qui s’appliquent à un membre, ou à des paramètres du membre.

- Noms des paramètres

- Types de retour des procédures

Le mot clé `Overloads` est facultatif lors de la surcharge, mais si un membre surchargé utilise le mot clé `Overloads`, tous les autres membres surchargés portant le même nom doivent également spécifier ce mot clé.

Les classes dérivées peuvent surcharger les membres hérités avec des membres qui ont des paramètres et des types de paramètres identiques, un processus appelé *occultation par nom et signature*. Si le mot clé `Overloads` est utilisé lors de l’occultation par nom et signature, l’implémentation du membre de la classe dérivée est utilisée à la place de l’implémentation dans la classe de base, et toutes les autres surcharges pour ce membre sont disponibles pour les instances de la classe dérivée.

Si le mot clé `Overloads` est omis lors de la surcharge d’un membre hérité avec un membre ayant des paramètres et des types de paramètres identiques, la surcharge est appelée *occultation par nom*. L’occultation par nom remplace l’implémentation héritée d’un membre, et rend toutes les autres surcharges indisponibles pour les instances de la classe dérivée et son decedents.

Les modificateurs `Overloads` et `Shadows` ne peuvent pas être utilisés à la fois avec la même propriété ou méthode.

### <a name="example"></a>Exemple

L’exemple suivant crée des méthodes surchargées qui acceptent une représentation `String` ou `Decimal` d’un montant en dollars et retournent une chaîne contenant les taxes de vente.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>Pour utiliser cet exemple afin de créer une méthode surchargée

1. Ouvrez un nouveau projet et ajoutez une classe nommée `TaxClass`.

2. Ajoutez le code suivant à la classe `TaxClass` .

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Ajoutez la procédure suivante à votre formulaire.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Ajoutez un bouton à votre formulaire et appelez la procédure `ShowTax` à partir de l’événement `Button1_Click` du bouton.

5. Exécutez le projet et cliquez sur le bouton du formulaire pour tester la procédure de `ShowTax` surchargée.

Au moment de l’exécution, le compilateur choisit la fonction surchargée appropriée qui correspond aux paramètres utilisés. Lorsque vous cliquez sur le bouton, la méthode surchargée est appelée en premier avec un paramètre `Price` qui est une chaîne et le message «Price est une chaîne. La taxe est $5,12» s’affiche. `TaxAmount` est appelé avec une valeur `Decimal` la deuxième fois et le message «Price est un nombre décimal. La taxe est $5,12» s’affiche.

## <a name="see-also"></a>Voir aussi

- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Occultation dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Éléments fondamentaux de l’héritage](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
