---
title: Vue d'ensemble des constantes
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic]
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
ms.openlocfilehash: 9ccddfe44757c76992d641094e21ec8c2110ef83
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338342"
---
# <a name="constants-overview-visual-basic"></a>Vue d'ensemble des constantes (Visual Basic)
Une constante est un nom explicite qui prend la place d’un nombre ou d’une chaîne qui ne change pas. Les constantes stockent des valeurs qui, comme leur nom l’indique, restent identiques tout au long de l’exécution d’une application. Vous pouvez améliorer la lisibilité de votre code et le rendre plus facile à gérer à l’aide de constantes. Utilisez-les dans du code qui contient des valeurs qui réapparaissent ou qui dépendent de certains nombres qui sont difficiles à mémoriser ou qui n’ont aucune signification évidente.  
  
## <a name="how-to-create-and-use-constants"></a>Comment créer et utiliser des constantes  
 Visual Basic contient un certain nombre de constantes prédéfinies, principalement pour l’impression et l’affichage. Vous pouvez également créer vos propres constantes avec l’instruction `Const`, en utilisant les mêmes instructions que pour la création d’un nom de variable. Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.  
  
 La portée d’une constante, qui est l’ensemble de tout le code qui peut faire référence à celle-ci sans qualifier son nom, est identique à celle d’une variable déclarée dans le même emplacement. Pour créer une constante qui existe dans l’étendue d’une procédure particulière, déclarez-la à l’intérieur de cette procédure. Pour créer une constante qui est disponible dans l’ensemble d’une application, déclarez-la à l’aide du mot clé `Public` dans la section déclarations de la classe.  
  
> [!NOTE]
> Bien que les constantes ressemblent à des variables, vous ne pouvez pas les modifier ou leur affecter de nouvelles valeurs comme vous le pouvez pour les variables.  
  
 Les constantes que vous utilisez dans votre code peuvent être définies par le modèle objet pour les contrôles ou les composants avec lesquels vous travaillez, ou ils peuvent être définis par l’utilisateur (autrement dit, ceux que vous créez vous-même).  
  
## <a name="compile-time-and-run-time-constants"></a>Constantes au moment de la compilation et au moment de l’exécution  
 Une constante au moment de la compilation est calculée au moment de la compilation du code, tandis qu’une constante d’exécution ne peut être calculée que pendant l’exécution de l’application. Une constante au moment de la compilation aura la même valeur chaque fois qu’une application s’exécute, alors qu’une constante d’exécution peut changer à chaque fois. Les constantes au moment de la compilation sont requises pour les cas tels que les limites de tableau, les expressions case ou les initialiseurs d’énumérateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Définition|Terme|  
|---|---|  
|[Guide pratique : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|Explique comment utiliser l’instruction `Const` pour déclarer une constante et définir sa valeur ; en déclarant une constante, vous assignez un nom explicite à la valeur.|  
|[Constantes définies par l’utilisateur](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|Décrit comment créer vos propres constantes, notamment des informations sur la portée et comment éviter les références circulaires.|  
|[Constantes et types de données littérales](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|Fournit des informations sur la façon dont le compilateur Visual Basic initialise des constantes lorsque `Option Explicit` est désactivé.|  
|[Guide pratique : regrouper les valeurs de constante connexes](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|Montre comment regrouper des valeurs constantes qui sont liées.|  
  
## <a name="reference"></a>Référence  
  
|Définition|Terme|  
|---|---|  
|[Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)|Répertorie les constantes prédéfinies par Visual Basic.|  
|[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md)|Décrit l’instruction `Const` et son utilisation.|  
|[Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|Décrit l’instruction `Option Strict` et son utilisation.|  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
