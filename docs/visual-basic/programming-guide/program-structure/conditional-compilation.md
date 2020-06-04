---
title: Compilation conditionnelle
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: c3eb1eb57b3d76e762ed53edb3b168ad96abec39
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403263"
---
# <a name="conditional-compilation-in-visual-basic"></a>Compilation conditionnelle en Visual Basic
Dans la *compilation conditionnelle*, les blocs de code particuliers d’un programme sont compilés de manière sélective, tandis que d’autres sont ignorés.  
  
 Par exemple, vous pouvez écrire des instructions de débogage qui comparent la vitesse des différentes approches de la même tâche de programmation, ou vous pouvez souhaiter localiser une application pour plusieurs langues. Les instructions de compilation conditionnelle sont conçues pour s’exécuter pendant la compilation, et non au moment de l’exécution.  
  
 Vous désignez des blocs de code à compiler de façon conditionnelle avec la `#If...Then...#Else` directive. Par exemple, pour créer des versions en français et en allemand de la même application à partir du même code source, vous incorporez des segments de code spécifiques à la plateforme dans des `#If...Then` instructions à l’aide des constantes prédéfinies `FrenchVersion` et `GermanVersion` . L’exemple suivant montre comment :  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 Si vous affectez à la valeur de la `FrenchVersion` constante de compilation conditionnelle la valeur `True` au moment de la compilation, le code conditionnel de la version française est compilé. Si vous affectez `GermanVersion` à la constante la valeur `True` , le compilateur utilise la version allemande. Si aucun n’a `True` la valeur, le code du dernier `Else` bloc s’exécute.  
  
> [!NOTE]
> La saisie semi-automatique ne fonctionne pas lors de la modification du code et de l’utilisation de directives de compilation conditionnelle si le code ne fait pas partie de la branche active.  
  
## <a name="declaring-conditional-compilation-constants"></a>Déclaration des constantes de compilation conditionnelle  
 Vous pouvez définir des constantes de compilation conditionnelle de l’une des trois façons suivantes :  
  
- Dans le **Concepteur de projets**  
  
- Au niveau de la ligne de commande lors de l’utilisation du compilateur de ligne de commande  
  
- Dans votre code  
  
 Les constantes de compilation conditionnelle ont une portée spéciale et ne sont pas accessibles à partir du code standard. La portée d’une constante de compilation conditionnelle dépend de la façon dont elle est définie. Le tableau suivant répertorie l’étendue des constantes déclarées à l’aide de chacune des trois méthodes mentionnées ci-dessus.  
  
|Définition de la constante|Étendue de la constante|  
|---|---|  
|**Concepteur de projets**|Public pour tous les fichiers du projet|  
|Ligne de commande|Public pour tous les fichiers passés au compilateur de ligne de commande|  
|`#Const`instruction dans le code|Privé pour le fichier dans lequel il est déclaré|  
  
|Pour définir des constantes dans le concepteur de projets|  
|---|  
|-Avant de créer votre fichier exécutable, définissez les constantes dans le **Concepteur de projet** en suivant les étapes indiquées dans [gestion des propriétés de projet et de solution](/visualstudio/ide/managing-project-and-solution-properties).|  
  
|Pour définir des constantes au niveau de la ligne de commande|  
|---|  
|-Utilisez le commutateur **-d** pour entrer des constantes de compilation conditionnelle, comme dans l’exemple suivant :<br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     Aucun espace n’est requis entre le commutateur **-d** et la première constante. Pour plus d’informations, consultez [-define (Visual Basic)](../../reference/command-line-compiler/define.md).<br />     Les déclarations de ligne de commande remplacent les déclarations entrées dans le **Concepteur de projet**, mais ne les efface pas. Les arguments définis dans le **Concepteur de projets** restent en vigueur pour les compilations suivantes.<br />     Lors de l’écriture de constantes dans le code lui-même, il n’existe pas de règles strictes quant à leur position, car leur étendue est le module entier dans lequel elles sont déclarées.|  
  
|Pour définir des constantes dans votre code|  
|---|  
|-Placez les constantes dans le bloc de déclaration du module dans lequel elles sont utilisées. Cela permet d’organiser votre code et de le rendre plus facile à lire.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Intitulé|Description|  
|---|---|  
|[Structure de programme et conventions de code](program-structure-and-code-conventions.md)|Fournit des suggestions pour faciliter la lecture et la maintenance de votre code.|  
  
## <a name="reference"></a>Informations de référence  
 [#Const directive](../../language-reference/directives/const-directive.md)  
  
 [#If... Then... #Else directives](../../language-reference/directives/if-then-else-directives.md)  
  
 [-définir (Visual Basic)](../../reference/command-line-compiler/define.md)
