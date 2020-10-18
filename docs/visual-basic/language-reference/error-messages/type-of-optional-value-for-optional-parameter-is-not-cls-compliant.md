---
title: Le type de la valeur facultative pour le paramètre optionnel <parametername> n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: e4fd7f0fd219eba7f20b62e0357d2139a21c0af7
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162685"
---
# <a name="bc40042-type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a>BC40042 : le type de la valeur facultative pour le paramètre facultatif \<parametername> n’est pas conforme CLS

Une procédure est marquée comme `<CLSCompliant(True)>` mais déclare un paramètre [facultatif](../modifiers/optional.md) avec la valeur par défaut d’un type non conforme.

 Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)), elle doit utiliser uniquement des types conformes à CLS. Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales. Elle s’applique également aux valeurs par défaut des paramètres facultatifs.

 Les types de données Visual Basics suivants ne sont pas conformes CLS :

- [SByte (type de données)](../data-types/sbyte-data-type.md)

- [UInteger (type de données)](../data-types/uinteger-data-type.md)

- [ULong (type de données)](../data-types/ulong-data-type.md)

- [UShort (type de données)](../data-types/ushort-data-type.md)

 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.

 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40042

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si le paramètre facultatif doit avoir une valeur par défaut de ce type particulier, supprimez <xref:System.CLSCompliantAttribute> . La procédure ne peut pas être conforme à CLS.

- Si la procédure doit être conforme à CLS, remplacez le type de cette valeur par défaut par le type conforme à CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.

- Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework. Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements. Si vous acceptez un entier 16 bits d’un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code Visual Basic managé.
