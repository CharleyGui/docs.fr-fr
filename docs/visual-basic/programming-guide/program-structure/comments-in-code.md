---
title: Commentaires dans le code (Visual Basic)
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
ms.openlocfilehash: 3635d52532789133a345d9a9228efae869c8c223
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945616"
---
# <a name="comments-in-code-visual-basic"></a>Commentaires dans le code (Visual Basic)
Lorsque vous lisez les exemples de code, vous rencontrez souvent le symbole de commentaire (`'`). Ce symbole indique au compilateur Visual Basic d’ignorer le texte qui le suit ou le *Commentaire*. Les commentaires sont de courtes explications destinées à éclairer ceux qui lisent le code.  
  
 En programmation, il est hautement recommandé de faire précéder toutes les procédures d'un commentaire court qui décrit les caractéristiques fonctionnelles de la procédure (ce qu'elle fait). Ceci est utile tant pour l'auteur du code lui-même que pour toute autre personne amenée à consulter le code. Vous devez séparer les détails relatifs à l'implémentation (comment la procédure fait ce qu'elle doit faire) des commentaires décrivant les caractéristiques fonctionnelles. Si vous fournissez des informations d'implémentation dans la description, n'oubliez pas de les mettre à jour lors de la mise à jour de la fonction.  
  
 Les commentaires peuvent soit suivre une instruction sur la même ligne, soit occuper une ligne entière. Ces deux cas sont illustrés par le code suivant :  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Si votre commentaire doit occuper plusieurs lignes, utilisez le symbole de commentaire sur chacune d'elles, comme l'exemple ci-dessous l'illustre.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Recommandations sur le commentaire  
 Le tableau suivant fournit des recommandations générales sur les types de commentaires qui peuvent précéder une section de code. Il s’agit de suggestions; Visual Basic n’applique pas les règles d’ajout de commentaires. Procédez de la façon que vous jugez la plus efficace pour vous et toute personne amenée à lire votre code.  
  
|||  
|---|---|  
|Type de commentaire|Description du commentaire|  
|Objectif|Décrit ce que fait la procédure (et non comment elle le fait)|  
|Hypothèses|Répertorie chaque variable externe, contrôle, fichier ouvert ou autre élément auquel la procédure accède.|  
|Effects (Effets)|Répertorie chaque variable externe, contrôle ou fichier affecté, ainsi que ses effets (uniquement si ce n'est pas évident)|  
|Entrées|Spécifie l’objectif attaché à l’argument|  
|Returns (Retours)|Explique les valeurs retournées par la procédure.|  
  
 N'oubliez pas :  
  
- Pour chaque déclaration de variable importante, faites précéder d'un commentaire décrivant son utilisation.  
  
- Les noms des variables, contrôles et procédures doivent être suffisamment clairs pour que les commentaires servent uniquement à fournir des détails d'implémentation complexes.  
  
- Vous ne pouvez pas faire suivre une séquence de continuation par un commentaire sur la même ligne.  
  
 Vous pouvez ajouter ou supprimer des symboles de commentaires pour un bloc de code en sélectionnant une ou plusieurs lignes de code et en![choisissant le commentaire (le Visual Basic bouton commentaire](./media/comments-in-code/visual-basic-comment-button.gif)dans Visual Studio) et![en supprimant les marques de **Commentaire** (le visuel Bouton Annuler les marques de commentaire de base dans Visual Studio. ) de la barre d’outils de **modification.** ](./media/comments-in-code/visual-basic-uncomment-button.gif)  
  
> [!NOTE]
> Vous pouvez également ajouter des commentaires à votre code en faisant précéder le texte du mot clé `REM`. Toutefois, les `'` boutons supprimer les**marques** de commentaire des symboles et des **Commentaires**/sont plus faciles à utiliser et nécessitent moins d’espace et de mémoire.  
  
## <a name="see-also"></a>Voir aussi

- [Instincts de base: documentation de votre code avec des commentaires XML](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [Guide pratique pour Créer une documentation XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Étiquettes XML pour les commentaires](../../../visual-basic/language-reference/xmldoc/index.md)
- [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [REM (instruction)](../../../visual-basic/language-reference/statements/rem-statement.md)
