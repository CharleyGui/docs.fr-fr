---
title: Structure d'un programme Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], Visual Basic
- program structure [Visual Basic], Visual Basic
- procedures [Visual Basic], structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
ms.openlocfilehash: 90bc1fd62a05f670424e1fac368376401d1030c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097772"
---
# <a name="structure-of-a-visual-basic-program"></a>Structure d'un programme Visual Basic

Un programme Visual Basic est créé à partir de blocs de construction standard. Une *solution* comprend un ou plusieurs projets. Un *projet* à son tour peut contenir un ou plusieurs assemblys. Chaque *assembly* est compilé à partir d’un ou de plusieurs fichiers sources. Un *fichier source* fournit la définition et l’implémentation des classes, des structures, des modules et des interfaces, qui contiennent finalement tout votre code.  
  
 Pour plus d’informations sur ces blocs de construction d’un programme Visual Basic, consultez [solutions et projets](/visualstudio/ide/solutions-and-projects-in-visual-studio) et [assemblys dans .net](../../../standard/assembly/index.md).  
  
## <a name="file-level-programming-elements"></a>Éléments de programmation au niveau du fichier  

 Quand vous démarrez un projet ou un fichier et ouvrez l’éditeur de code, vous voyez du code déjà en place et dans le bon ordre. Tout code que vous écrivez doit suivre la séquence suivante :  
  
1. `Option` publication  
  
2. `Imports` publication  
  
3. `Namespace` instructions et éléments au niveau de l’espace de noms  
  
 Si vous entrez des instructions dans un ordre différent, les erreurs de compilation peuvent se produire.  
  
 Un programme peut également contenir des instructions de compilation conditionnelle. Vous pouvez les intercaler dans le fichier source entre les instructions de la séquence précédente.  
  
### <a name="option-statements"></a>Instructions option  

 `Option` les instructions établissent des règles de fond pour le code suivant, ce qui contribue à éviter les erreurs de syntaxe et de logique. L' [instruction Option Explicit](../../language-reference/statements/option-explicit-statement.md) garantit que toutes les variables sont déclarées et épelées correctement, ce qui réduit le temps de débogage. L' [instruction Option Strict](../../language-reference/statements/option-strict-statement.md) permet de réduire les erreurs logiques et la perte de données qui peuvent se produire lorsque vous travaillez entre des variables de types de données différents. L' [instruction Option Compare](../../language-reference/statements/option-compare-statement.md) spécifie la façon dont les chaînes sont comparées les unes aux autres, en fonction de leurs `Binary` `Text` valeurs ou.  
  
### <a name="imports-statements"></a>Instructions Imports  

 Vous pouvez inclure une [instruction Imports (espace de noms et type .net)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer des noms définis en dehors de votre projet. Une `Imports` instruction permet à votre code de faire référence à des classes et d’autres types définis dans l’espace de noms importé, sans avoir à les qualifier. Vous pouvez utiliser autant d' `Imports` instructions que nécessaire. Pour plus d’informations, consultez [références et l’instruction Imports](references-and-the-imports-statement.md).  
  
### <a name="namespace-statements"></a>Instructions d’espace de noms  

 Les espaces de noms vous aident à organiser et à classer vos éléments de programmation pour faciliter le regroupement et l’accès. Vous utilisez l' [instruction Namespace](../../language-reference/statements/namespace-statement.md) pour classer les instructions suivantes dans un espace de noms particulier. Pour plus d’informations, consultez l’article [Espaces de noms dans Visual Basic](namespaces.md).  
  
### <a name="conditional-compilation-statements"></a>Instructions de compilation conditionnelle  

 Les instructions de compilation conditionnelle peuvent apparaître presque n’importe où dans votre fichier source. Elles entraînent l’inclusion ou l’exclusion de certaines parties de votre code au moment de la compilation en fonction de certaines conditions. Vous pouvez également les utiliser pour déboguer votre application, car le code conditionnel s’exécute en mode de débogage uniquement. Pour plus d’informations, consultez [compilation conditionnelle](conditional-compilation.md).  
  
## <a name="namespace-level-programming-elements"></a>Éléments de programmation au niveau de l’espace de noms  

 Les classes, les structures et les modules contiennent tout le code dans votre fichier source. Il s’agit d’éléments *au niveau* de l’espace de noms, qui peuvent apparaître dans un espace de noms ou au niveau du fichier source. Ils contiennent les déclarations de tous les autres éléments de programmation. Les interfaces, qui définissent des signatures d’élément mais ne fournissent pas d’implémentation, s’affichent également au niveau du module. Pour plus d’informations sur les éléments de niveau module, consultez les rubriques suivantes :  
  
- [Class (instruction)](../../language-reference/statements/class-statement.md)  
  
- [Structure, instruction](../../language-reference/statements/structure-statement.md)  
  
- [Module, instruction](../../language-reference/statements/module-statement.md)  
  
- [Interface (instruction)](../../language-reference/statements/interface-statement.md)  
  
 Les éléments de données au niveau de l’espace de noms sont des énumérations et des délégués.  
  
## <a name="module-level-programming-elements"></a>Éléments de programmation au niveau du module  

 Les procédures, les opérateurs, les propriétés et les événements sont les seuls éléments de programmation qui peuvent contenir du code exécutable (les instructions qui exécutent des actions au moment de l’exécution). Il s’agit des éléments de *niveau module* de votre programme. Pour plus d’informations sur les éléments de niveau procédure, consultez les rubriques suivantes :  
  
- [Function (instruction)](../../language-reference/statements/function-statement.md)  
  
- [Sub (instruction)](../../language-reference/statements/sub-statement.md)  
  
- [Declare Statement](../../language-reference/statements/declare-statement.md)  
  
- [Operator Statement](../../language-reference/statements/operator-statement.md)  
  
- [Property Statement](../../language-reference/statements/property-statement.md)  
  
- [Event, instruction](../../language-reference/statements/event-statement.md)  
  
 Les éléments de données au niveau du module sont les variables, les constantes, les énumérations et les délégués.  
  
## <a name="procedure-level-programming-elements"></a>Éléments de programmation au niveau de la procédure  

 La majeure partie du contenu des éléments de *niveau procédure* sont des instructions exécutables qui constituent le code d’exécution de votre programme. Tout le code exécutable doit être dans une procédure ( `Function` , `Sub` , `Operator` , `Get` , `Set` , `AddHandler` , `RemoveHandler` , `RaiseEvent` ). Pour plus d’informations, consultez [Instructions](../language-features/statements.md).  
  
 Les éléments de données au niveau de la procédure sont limités aux constantes et variables locales.  
  
## <a name="the-main-procedure"></a>La procédure principale  

 La `Main` procédure est le premier code à s’exécuter lorsque votre application a été chargée. `Main` sert de point de départ et de contrôle global pour votre application. Il existe quatre types de `Main` :  
  
- `Sub Main()`  
  
- `Sub Main(ByVal cmdArgs() As String)`  
  
- `Function Main() As Integer`  
  
- `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 La variété la plus courante de cette procédure est `Sub Main()` . Pour plus d’informations, consultez la [procédure main dans Visual Basic](main-procedure.md).  
  
## <a name="see-also"></a>Voir aussi

- [Procédure Main dans Visual Basic](main-procedure.md)
- [Conventions d'affectation de noms Visual Basic](naming-conventions.md)
- [Restrictions liées à Visual Basic](limitations.md)
