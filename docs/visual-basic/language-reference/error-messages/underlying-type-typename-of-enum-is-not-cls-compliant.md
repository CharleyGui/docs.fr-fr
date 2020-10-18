---
title: Le type sous-jacent <typename> d'Enum n'est pas conforme CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 42c2398945b97d68161af6fb3c3b69909f4aaf39
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161515"
---
# <a name="bc40032-underlying-type-typename-of-enum-is-not-cls-compliant"></a>BC40032 : le type sous-jacent \<typename> de l’enum n’est pas conforme CLS

Le type de données spécifié pour cette énumération ne fait pas partie de l' [indépendance du langage et des composants de Language-Independent](../../../standard/language-independence-and-language-independent-components.md) (CLS). Il ne s’agit pas d’une erreur au sein de votre composant, car les .NET Framework et Visual Basic prennent en charge ce type de données. Toutefois, un autre composant écrit dans du code strictement conforme CLS peut ne pas prendre en charge ce type de données. Un tel composant peut ne pas être en mesure d’interagir correctement avec votre composant.

 Les types de données Visual Basics suivants ne sont pas conformes CLS :

- [SByte (type de données)](../data-types/sbyte-data-type.md)

- [UInteger (type de données)](../data-types/uinteger-data-type.md)

- [ULong (type de données)](../data-types/ulong-data-type.md)

- [UShort (type de données)](../data-types/ushort-data-type.md)

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC40032

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si votre composant ne s’interface qu’avec d’autres composants de .NET Framework ou n’interagit pas avec d’autres composants, vous n’avez pas besoin de modifier quoi que ce soit.

- Si vous interagissez avec un composant qui n’est pas écrit pour le .NET Framework, vous pouvez être en mesure de déterminer, soit par réflexion, soit à partir de la documentation, s’il prend en charge ce type de données. Si c’est le cas, vous n’avez pas besoin de modifier quoi que ce soit.

- Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche. Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647. Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.

- Si vous utilisez des objets Automation ou COM, gardez à l’esprit que certains types ont des largeurs de données différentes de celles de la .NET Framework. Par exemple, `uint` correspond souvent à 16 bits dans d’autres environnements. Si vous passez un argument de 16 bits à un tel composant, déclarez-le comme `UShort` au lieu de `UInteger` dans votre code Visual Basic managé.

## <a name="see-also"></a>Voir aussi

- [Réflexion (Visual Basic)](../../programming-guide/concepts/reflection.md)
- [Réflexion](../../../framework/reflection-and-codedom/reflection.md)
