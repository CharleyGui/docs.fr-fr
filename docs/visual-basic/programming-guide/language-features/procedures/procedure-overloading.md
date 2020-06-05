---
title: Surcharge de procédure
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
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363874"
---
# <a name="procedure-overloading-visual-basic"></a>Surcharge de procédure (Visual Basic)

La *surcharge* d’une procédure signifie la définir dans plusieurs versions, en utilisant le même nom mais des listes de paramètres différentes. L’objectif de la surcharge est de définir plusieurs versions étroitement liées d’une procédure sans avoir à les différencier par nom. Pour ce faire, vous devez faire varier la liste de paramètres.

## <a name="overloading-rules"></a>Surcharge des règles

Lorsque vous surchargez une procédure, les règles suivantes s’appliquent :

- **Même nom**. Chaque version surchargée doit utiliser le même nom de procédure.

- **Signature différente**. Chaque version surchargée doit être différente de toutes les autres versions surchargées dans au moins l’un des aspects suivants :

  - Nombre de paramètres

  - Ordre des paramètres

  - Types de données des paramètres

  - Nombre de paramètres de type (pour une procédure générique)

  - Type de retour (uniquement pour un opérateur de conversion)

  Avec le nom de la procédure, les éléments précédents sont appelés collectivement la *signature* de la procédure. Quand vous appelez une procédure surchargée, le compilateur utilise la signature pour vérifier que l’appel correspond correctement à la définition.

- **Éléments ne faisant pas partie de la signature**. Vous ne pouvez pas surcharger une procédure sans faire varier la signature. En particulier, vous ne pouvez pas surcharger une procédure en faisant varier un ou plusieurs des éléments suivants :

  - Mots clés de modificateur de procédure, tels que `Public` , `Shared` et`Static`

  - Noms de paramètre ou de paramètre de type

  - Contraintes de paramètre de type (pour une procédure générique)

  - Mots clés de modificateur de paramètre, tels que `ByRef` et`Optional`

  - Si elle retourne une valeur

  - Type de données de la valeur de retour (à l’exception d’un opérateur de conversion)

  Les éléments de la liste précédente ne font pas partie de la signature. Même si vous ne pouvez pas les utiliser pour différencier les versions surchargées, vous pouvez les faire varier parmi les versions surchargées qui sont correctement différenciées par leurs signatures.

- **Arguments à liaison tardive**. Si vous envisagez de passer une variable objet à liaison tardive à une version surchargée, vous devez déclarer le paramètre approprié comme <xref:System.Object> .

## <a name="multiple-versions-of-a-procedure"></a>Plusieurs versions d’une procédure

Supposons que vous écriviez une `Sub` procédure de publication d’une transaction sur le solde d’un client et que vous souhaitez être en mesure de faire référence au client par son nom ou par son numéro de compte. Pour ce faire, vous pouvez définir deux `Sub` procédures différentes, comme dans l’exemple suivant :

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Versions surchargées

Une alternative consiste à surcharger un nom de procédure unique. Vous pouvez utiliser le mot clé [Overloads](../../../language-reference/modifiers/overloads.md) pour définir une version de la procédure pour chaque liste de paramètres, comme suit :

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Surcharges supplémentaires

Si vous souhaitez également accepter un montant de transaction dans `Decimal` ou `Single` , vous pouvez effectuer une surcharge supplémentaire `post` pour permettre cette variation. Si vous l’avez fait pour chacune des surcharges de l’exemple précédent, vous avez quatre `Sub` procédures, toutes avec le même nom, mais avec quatre signatures différentes.

## <a name="advantages-of-overloading"></a>Avantages de la surcharge

L’avantage de la surcharge d’une procédure est de la flexibilité de l’appel. Pour utiliser la `post` procédure déclarée dans l’exemple précédent, le code appelant peut obtenir l’identification du client en tant que `String` ou `Integer` , puis appeler la même procédure dans les deux cas. L'exemple suivant illustre ce mécanisme :

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Comment : définir plusieurs versions d'une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md)
- [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Résolution de surcharge](./overload-resolution.md)
- [Surcharges](../../../language-reference/modifiers/overloads.md)
- [Generic Types in Visual Basic](../data-types/generic-types.md)
