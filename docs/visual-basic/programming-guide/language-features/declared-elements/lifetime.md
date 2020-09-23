---
title: Durée de vie
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 67fe63eecd2aa0c134682708cdeddb21ba06db12
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087490"
---
# <a name="lifetime-in-visual-basic"></a>Durée de vie dans Visual Basic

La durée de *vie* d’un élément déclaré est la période pendant laquelle il peut être utilisé. Les variables sont les seuls éléments qui ont une durée de vie. À cet effet, le compilateur traite les paramètres de procédure et les retours de fonction comme des cas spéciaux de variables. La durée de vie d’une variable représente la durée pendant laquelle elle peut contenir une valeur. Sa valeur peut changer pendant sa durée de vie, mais elle contient toujours une valeur.  
  
## <a name="different-lifetimes"></a>Durées de vie différentes  

 Une *variable membre* (déclarée au niveau du module, en dehors de toute procédure) a généralement la même durée de vie que l’élément dans lequel elle est déclarée. Une variable non partagée déclarée dans une classe ou une structure existe en tant que copie distincte pour chaque instance de la classe ou de la structure dans laquelle elle est déclarée. Chaque variable de ce type a la même durée de vie que son instance. Toutefois, une `Shared` variable n’a qu’une seule durée de vie, qui dure pendant toute la durée d’exécution de votre application.  
  
 Une *variable locale* (déclarée à l’intérieur d’une procédure) existe uniquement pendant l’exécution de la procédure dans laquelle elle est déclarée. Cela s’applique également aux paramètres de cette procédure et à tout retour de fonction. Toutefois, si cette procédure appelle d’autres procédures, les variables locales conservent leurs valeurs pendant l’exécution des procédures appelées.  
  
## <a name="beginning-of-lifetime"></a>Début de la durée de vie  

 La durée de vie d’une variable locale commence lorsque le contrôle entre dans la procédure dans laquelle elle est déclarée. Chaque variable locale est initialisée à la valeur par défaut pour son type de données dès que la procédure commence à s’exécuter. Lorsque la procédure rencontre une `Dim` instruction qui spécifie des valeurs initiales, elle définit ces variables sur ces valeurs, même si votre code s’est déjà vu assigner d’autres valeurs.  
  
 Chaque membre d’une variable de structure est initialisé comme s’il s’agissait d’une variable distincte. De même, chaque élément d’une variable de tableau est initialisé individuellement.  
  
 Les variables déclarées dans un bloc à l’intérieur d’une procédure (telle qu’une `For` boucle) sont initialisées à l’entrée de la procédure. Ces initialisations prennent effet, que votre code exécute ou non le bloc.  
  
## <a name="end-of-lifetime"></a>Fin de la durée de vie  

 Lorsqu’une procédure se termine, les valeurs de ses variables locales ne sont pas conservées et Visual Basic récupère leur mémoire. La prochaine fois que vous appelez la procédure, toutes ses variables locales sont créées et réinitialisées.  
  
 Lorsqu’une instance d’une classe ou d’une structure se termine, ses variables non partagées perdent leur mémoire et leurs valeurs. Chaque nouvelle instance de la classe ou de la structure crée et réinitialise ses variables non partagées. Toutefois, les `Shared` variables sont conservées jusqu’à ce que votre application cesse de s’exécuter.  
  
## <a name="extension-of-lifetime"></a>Extension de la durée de vie  

 Si vous déclarez une variable locale avec le `Static` mot clé, sa durée de vie est plus longue que la durée d’exécution de sa procédure. Le tableau suivant montre comment la déclaration de procédure détermine le temps pendant lequel une `Static` variable existe.  
  
|Emplacement et partage des procédures|La durée de vie des variables statiques commence|Fin de la durée de vie des variables statiques|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|Dans un module (partagé par défaut)|La première fois que la procédure est appelée|Quand votre application cesse de s’exécuter|  
|Dans une classe, `Shared` (la procédure n’est pas un membre d’instance)|La première fois que la procédure est appelée sur une instance spécifique ou sur le nom de la classe ou de la structure elle-même|Quand votre application cesse de s’exécuter|  
|Dans une instance d’une classe, not `Shared` (la procédure est un membre d’instance)|La première fois que la procédure est appelée sur l’instance spécifique|Lorsque l’instance est libérée pour garbage collection (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Variables statiques du même nom  

 Vous pouvez déclarer des variables statiques portant le même nom dans plusieurs procédures. Dans ce cas, le compilateur Visual Basic considère chaque variable de ce type comme un élément distinct. L’initialisation de l’une de ces variables n’affecte pas les valeurs des autres. Il en va de même si vous définissez une procédure avec un ensemble de surcharges et que vous déclarez une variable statique avec le même nom dans chaque surcharge.  
  
## <a name="containing-elements-for-static-variables"></a>Contenant des éléments pour les variables statiques  

 Vous pouvez déclarer une variable locale statique dans une classe, c’est-à-dire à l’intérieur d’une procédure de cette classe. Toutefois, vous ne pouvez pas déclarer une variable locale statique dans une structure, qu’il s’agisse d’un membre de structure ou d’une variable locale d’une procédure au sein de cette structure.  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  

 L’exemple suivant déclare une variable avec le mot clé [static](../../../language-reference/modifiers/static.md) . (Notez que vous n’avez pas besoin du `Dim` mot clé lorsque l' [instruction Dim](../../../language-reference/statements/dim-statement.md) utilise un modificateur tel que `Static` .)  
  
### <a name="code"></a>Code  

 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Commentaires  

 Dans l’exemple précédent, la variable `applesSold` continue d’exister après le `runningTotal` retour de la procédure au code appelant. La prochaine fois que `runningTotal` est appelé, `applesSold` conserve sa valeur précédemment calculée.  
  
 Si `applesSold` a été déclaré sans utiliser `Static` , les valeurs accumulées précédentes ne seront pas conservées entre les appels à `runningTotal` . La prochaine fois `runningTotal` que a été appelé, `applesSold` aurait été recréé et initialisé à 0, et `runningTotal` aurait simplement retourné la même valeur que celle avec laquelle il a été appelé.  
  
### <a name="compile-the-code"></a>Compiler le code  

 Vous pouvez initialiser la valeur d’une variable locale statique dans le cadre de sa déclaration. Si vous déclarez un tableau comme étant `Static` , vous pouvez initialiser son rang (nombre de dimensions), la longueur de chaque dimension et les valeurs des éléments individuels.  
  
### <a name="security"></a>Sécurité  

 Dans l’exemple précédent, vous pouvez produire la même durée de vie en déclarant `applesSold` au niveau du module. Toutefois, si vous avez modifié l’étendue d’une variable de cette manière, la procédure n’aura plus d’accès exclusif à celle-ci. Étant donné que d’autres procédures peuvent accéder à `applesSold` sa valeur et la modifier, le total cumulé peut être non fiable et le code peut être plus difficile à gérer.  
  
## <a name="see-also"></a>Voir aussi

- [Partagé](../../../language-reference/modifiers/shared.md)
- [Nothing](../../../language-reference/nothing.md)
- [Declared Element Names](declared-element-names.md)
- [References to Declared Elements](references-to-declared-elements.md)
- [Portée dans Visual Basic](scope.md)
- [Niveaux d’accès dans Visual Basic](access-levels.md)
- [Variables](../variables/index.md)
- [Déclaration de variable](../variables/variable-declaration.md)
- [Dépannage des types de données](../data-types/troubleshooting-data-types.md)
- [Statique](../../../language-reference/modifiers/static.md)
