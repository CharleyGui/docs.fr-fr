---
title: Structures et classes
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3353935a74bb77fa4a630e706aa425063c7a610a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346327"
---
# <a name="structures-and-classes-visual-basic"></a>Structures et classes (Visual Basic)
Visual Basic unifie la syntaxe des structures et des classes, avec pour résultat que les deux entités prennent en charge la plupart des mêmes fonctionnalités. Toutefois, il existe également des différences importantes entre les structures et les classes.  
  
 Les classes présentent l’avantage d’être des types référence, le passage d’une référence est plus efficace que la transmission d’une variable de structure avec toutes ses données. En revanche, les structures ne nécessitent pas d’allocation de mémoire sur le tas global.  
  
 Étant donné que vous ne pouvez pas hériter d’une structure, les structures doivent être utilisées uniquement pour les objets qui n’ont pas besoin d’être étendus. Utilisez des structures lorsque l’objet que vous souhaitez créer a une petite taille d’instance et prenez en compte les caractéristiques de performance des classes par rapport aux structures.  
  
## <a name="similarities"></a>Similitudes  
 Les structures et les classes sont similaires aux points suivants :  
  
- Les deux sont des types de *conteneurs* , ce qui signifie qu’ils contiennent d’autres types en tant que membres.  
  
- Tous deux ont des membres, qui peuvent inclure des constructeurs, des méthodes, des propriétés, des champs, des constantes, des énumérations, des événements et des gestionnaires d’événements. Toutefois, ne confondez pas ces membres avec les *éléments* déclarés d’une structure.  
  
- Les membres des deux peuvent avoir des niveaux d’accès individualisés. Par exemple, un membre peut être déclaré `Public` et un autre `Private`.  
  
- Les deux peuvent implémenter des interfaces.  
  
- Les deux peuvent avoir des constructeurs partagés, avec ou sans paramètres.  
  
- Les deux peuvent exposer une *propriété par défaut*, à condition que la propriété prenne au moins un paramètre.  
  
- Les deux peuvent déclarer et déclencher des événements, et les deux peuvent déclarer des délégués.  
  
## <a name="differences"></a>Différences  
 Les structures et les classes diffèrent dans les éléments suivants :  
  
- Les structures sont des *types valeur*; les classes sont des *types référence*. Une variable d’un type structure contient les données de la structure, au lieu de contenir une référence aux données en tant que type de classe.  
  
- Les structures utilisent l’allocation de pile ; les classes utilisent l’allocation de tas.  
  
- Tous les éléments de structure sont `Public` par défaut ; les constantes et les variables de classe sont `Private` par défaut, tandis que les autres membres de classe sont `Public` par défaut. Ce comportement pour les membres de classe assure la compatibilité avec le système Visual Basic 6,0 des valeurs par défaut.  
  
- Une structure doit avoir au moins une variable non partagée ou un élément événement non personnalisé non partagé ; une classe peut être complètement vide.  
  
- Les éléments de structure ne peuvent pas être déclarés comme `Protected`; les membres de classe peuvent.  
  
- Une procédure de structure ne peut gérer des événements que s’il s’agit d’une procédure de`Sub` [partagée](../../../../visual-basic/language-reference/modifiers/shared.md) , et uniquement au moyen de l' [instruction AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md); toute procédure de classe peut gérer des événements, à l’aide du mot clé [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) ou de l’instruction `AddHandler`. Pour plus d'informations, consultez [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
- Les déclarations de variable de structure ne peuvent pas spécifier d’initialiseurs ou de tailles initiales pour les tableaux ; les déclarations de variable de classe peuvent.  
  
- Les structures héritent implicitement de la classe <xref:System.ValueType?displayProperty=nameWithType> et ne peuvent pas hériter d’un autre type ; les classes peuvent hériter d’une classe ou de classes autres que <xref:System.ValueType?displayProperty=nameWithType>.  
  
- Les structures ne peuvent pas être héritées ; les classes sont.  
  
- Les structures n’étant jamais terminées, le common language runtime (CLR) n’appelle jamais la méthode <xref:System.Object.Finalize%2A> sur toute structure ; les classes sont terminées par le garbage collector (GC), qui appelle <xref:System.Object.Finalize%2A> sur une classe lorsqu’elle détecte qu’il n’y a aucune référence active restante.  
  
- Une structure ne requiert pas de constructeur ; une classe.  
  
- Les structures peuvent avoir des constructeurs non partagés uniquement si elles acceptent des paramètres ; les classes peuvent les utiliser avec ou sans paramètres.  
  
 Chaque structure a un constructeur public implicite sans paramètres. Ce constructeur initialise tous les éléments de données de la structure à leurs valeurs par défaut. Vous ne pouvez pas redéfinir ce comportement.  
  
## <a name="instances-and-variables"></a>Instances et variables  
 Étant donné que les structures sont des types valeur, chaque variable de structure est définitivement liée à une instance de structure individuelle. Toutefois, les classes sont des types référence, et une variable objet peut faire référence à différentes instances de classe à des moments différents. Cette distinction affecte l’utilisation des structures et des classes des manières suivantes :  
  
- **D’initialisation.** Une variable de structure comprend implicitement une initialisation des éléments à l’aide du constructeur sans paramètre de la structure. Par conséquent, `Dim s As struct1` équivaut à `Dim s As struct1 = New struct1()`.  
  
- **Assignation de variables.** Lorsque vous assignez une variable de structure à une autre ou que vous transmettez une instance de structure à un argument de procédure, les valeurs actuelles de tous les éléments de variable sont copiées dans la nouvelle structure. Lorsque vous assignez une variable objet à une autre ou si vous transmettez une variable objet à une procédure, seul le pointeur de référence est copié.  
  
- **Attribution de la valeur Nothing.** Vous pouvez affecter la valeur [Nothing](../../../../visual-basic/language-reference/nothing.md) à une variable de structure, mais l’instance continue à être associée à la variable. Vous pouvez toujours appeler ses méthodes et accéder à ses éléments de données, bien que les éléments de variable soient réinitialisés par l’assignation.  
  
     En revanche, si vous définissez une variable objet sur `Nothing`, vous la dissociez d’une instance de classe, et vous ne pouvez pas accéder à des membres par le biais de la variable tant que vous n’affectez pas une autre instance à celle-ci.  
  
- **Instances multiples.** Une variable objet peut avoir différentes instances de classe qui lui sont assignées à des moments différents, et plusieurs variables objet peuvent faire référence à la même instance de classe en même temps. Les modifications que vous apportez aux valeurs des membres de la classe affectent ces membres quand ils sont accessibles par le biais d’une autre variable pointant vers la même instance.  
  
     Toutefois, les éléments de structure sont isolés dans leur propre instance. Les modifications apportées à leurs valeurs ne sont pas reflétées dans les autres variables de structure, même dans d’autres instances de la même déclaration de `Structure`.  
  
- **D’égalité.** Le test d’égalité de deux structures doit être effectué avec un test élément par élément. Deux variables objet peuvent être comparées à l’aide de la méthode <xref:System.Object.Equals%2A>. <xref:System.Object.Equals%2A> indique si les deux variables pointent vers la même instance.  
  
## <a name="see-also"></a>Voir aussi

- [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
