---
title: Le type de retour de la fonction '<procedurename>' n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9a877046a1b30e2e3773a41b8b44573e11ff1c96
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159701"
---
# <a name="bc40027-return-type-of-function-procedurename-is-not-cls-compliant"></a>BC40027 : le type de retour de la fonction' \<procedurename> 'n’est pas conforme CLS

Une `Function` procédure est marquée comme `<CLSCompliant(True)>` mais retourne un type qui est marqué comme `<CLSCompliant(False)>` , qui n’est pas marqué ou qui n’est pas qualifié car il s’agit d’un type non conforme.

 Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)), elle doit utiliser uniquement des types conformes à CLS. Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.

 Les types de données Visual Basics suivants ne sont pas conformes CLS :

- [SByte (type de données)](../data-types/sbyte-data-type.md)

- [UInteger (type de données)](../data-types/uinteger-data-type.md)

- [ULong (type de données)](../data-types/ulong-data-type.md)

- [UShort (type de données)](../data-types/ushort-data-type.md)

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40027

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si la `Function` procédure doit retourner ce type particulier, supprimez <xref:System.CLSCompliantAttribute> . La procédure ne peut pas être conforme à CLS.

- Si la `Function` procédure doit être conforme CLS, remplacez le type de retour par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.

- Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework. Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements. Si vous retournez un entier 16 bits à un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code Visual Basic managé.
