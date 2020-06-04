---
title: Le type de paramètre '<parametername>' n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: edbcadf271c4ccafc11e5b64eb103a0290976179
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413012"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a>Le type de paramètre '\<parametername>' n'est pas conforme CLS
Une procédure est marquée comme `<CLSCompliant(True)>` , mais déclare un paramètre avec un type qui est marqué comme `<CLSCompliant(False)>` , qui n’est pas marqué ou qui n’est pas qualifié car il s’agit d’un type non conforme.  
  
 Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](../../../standard/language-independence-and-language-independent-components.md)), elle doit utiliser uniquement des types conformes à CLS. Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.  
  
 Les types de données Visual Basics suivants ne sont pas conformes CLS :  
  
- [SByte (type de données)](../data-types/sbyte-data-type.md)  
  
- [UInteger (type de données)](../data-types/uinteger-data-type.md)  
  
- [ULong (type de données)](../data-types/ulong-data-type.md)  
  
- [UShort (type de données)](../data-types/ushort-data-type.md)  
  
 Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité. Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.  
  
 Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC40028  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Si la procédure doit prendre un paramètre de ce type particulier, supprimez <xref:System.CLSCompliantAttribute> . La procédure ne peut pas être conforme à CLS.  
  
- Si la procédure doit être conforme CLS, remplacez le type de ce paramètre par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.  
  
- Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework. Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements. Si vous acceptez un entier 16 bits d’un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code Visual Basic managé.
