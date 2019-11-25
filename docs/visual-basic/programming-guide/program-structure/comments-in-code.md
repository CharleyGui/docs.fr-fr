---
title: Commentaires dans le code
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 189810393db42c54cb8a0f97b22b3d1514d9a7c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346168"
---
# <a name="comments-in-code-visual-basic"></a>Commentaires dans le code (Visual Basic)
Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire (`'`). This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*. Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.  
  
 En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure (ce qu'elle fait). Ceci est utile tant pour l'auteur du code lui-même que pour toute autre personne amenée à consulter le code. Vous devez séparer les détails relatifs à l'implémentation (comment la procédure fait ce qu'elle doit faire) des commentaires décrivant les caractéristiques fonctionnelles. Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.  
  
 Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière. Ces deux cas sont illustrés par le code suivant :  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci-dessous l'illustre.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Recommandations sur le commentaire  
 Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code. These are suggestions; Visual Basic does not enforce rules for adding comments. Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.  
  
|||  
|---|---|  
|Type de commentaire|Description du commentaire|  
|Fonction|Décrit ce que fait la procédure (et non comment elle le fait)|  
|Assumptions (Hypothèses)|Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.|  
|Effects (Effets)|Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets (uniquement si ce n'est pas évident)|  
|Inputs (Entrées)|Spécifie l’objectif attaché à l’argument|  
|Returns (Retours)|Explique les valeurs retournées par la procédure.|  
  
 N'oubliez pas :  
  
- Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.  
  
- Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.  
  
- Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.  
  
 You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.  
  
> [!NOTE]
> Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`. However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.  
  
## <a name="see-also"></a>Voir aussi

- [Basic Instincts - Documenting Your Code With XML Comments](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [Guide pratique : créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
- [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [REM (instruction)](../../../visual-basic/language-reference/statements/rem-statement.md)
