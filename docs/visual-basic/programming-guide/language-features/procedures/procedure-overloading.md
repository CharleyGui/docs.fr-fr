---
title: Surcharge de procédure (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 91e76e8c051b1d6f8b6fc1604018a26b23b4945b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663304"
---
# <a name="procedure-overloading-visual-basic"></a>Surcharge de procédure (Visual Basic)

*La surcharge* une procédure consiste à définir celle-ci en plusieurs versions, à l’aide du même nom mais des listes de paramètres différentes. L’objectif de la surcharge consiste à définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom. Pour cela, en faisant varier la liste de paramètres.

## <a name="overloading-rules"></a>Règles de surcharge

Lorsque vous surchargez une procédure, les règles suivantes s’appliquent :

- **Nom de la même**. Chaque version surchargée doit utiliser le même nom de procédure.

- **Signature différente**. Chaque version surchargée doit différer de toutes les autres versions surchargées dans au moins un des points suivants :

  - Nombre de paramètres

  - Ordre des paramètres

  - Types de données des paramètres

  - Nombre de paramètres de type (pour une procédure générique)

  - Type de retour (uniquement pour un opérateur de conversion)

  Avec le nom de la procédure, les éléments précédents sont appelés collectivement le *signature* de la procédure. Lorsque vous appelez une procédure surchargée, le compilateur utilise la signature pour vérifier que l’appel correspond exactement à la définition.

- **Les éléments ne fait pas partie de la Signature de**. Vous ne pouvez pas surcharger une procédure sans faire varier la signature. En particulier, vous ne pouvez pas surcharger une procédure en faisant varier uniquement un ou plusieurs des éléments suivants :

  - Mots clés de modificateur de procédure, tel que `Public`, `Shared`, et `Static`

  - Paramètre de type ou des noms de paramètres

  - Contraintes de paramètre de type (pour une procédure générique)

  - Mots clés de modificateur de paramètre, tel que `ByRef` et `Optional`

  - Si elle retourne une valeur

  - le type de données de la valeur de retour (à l’exception d’un opérateur de conversion)

  Les éléments dans la liste précédente ne font pas partie de la signature. Bien que vous ne pouvez pas les utiliser pour faire la distinction entre les versions surchargées, vous pouvez les modifier parmi des versions surchargées qui sont correctement différenciées par leurs signatures.

- **À liaison tardive Arguments**. Si vous envisagez de passer une variable objet à liaison tardive à une version surchargée, vous devez déclarer le paramètre approprié en tant que <xref:System.Object>.

## <a name="multiple-versions-of-a-procedure"></a>Plusieurs Versions d’une procédure

Supposons que vous écrivez un `Sub` procédure pour valider une transaction sur le solde d’un client et que vous souhaitez être en mesure de faire référence au client par nom ou par numéro de compte. Pour ce faire, vous pouvez définir deux différents `Sub` procédures, comme dans l’exemple suivant :

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Versions surchargées

Une alternative consiste à surcharger un seul nom de procédure. Vous pouvez utiliser la [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) mot clé pour définir une version de la procédure pour chaque liste de paramètres, comme suit :

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Surcharges supplémentaires

Si vous voulez également accepter un montant de transaction dans le `Decimal` ou `Single`, vous pouvez surcharger davantage `post` pour permettre cette variation. Si vous l’avez fait pour chacune des surcharges dans l’exemple précédent, vous devez obtenir quatre `Sub` procédures, le tout avec le même nom mais avec quatre signatures différentes.

## <a name="advantages-of-overloading"></a>Avantages de la surcharge

L’avantage de la surcharge d’une procédure est la flexibilité de l’appel. À utiliser le `post` procédure déclarée dans l’exemple précédent, le code appelant peut obtenir l’identification du client selon un `String` ou un `Integer`, puis appelez la même procédure dans les deux cas. L'exemple suivant illustre ce comportement :

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Guide pratique pour Définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Guide pratique pour Appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Guide pratique pour Surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Guide pratique pour Surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Résolution de surcharge](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
