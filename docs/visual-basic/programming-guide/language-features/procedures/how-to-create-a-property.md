---
title: 'Comment : créer une propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: bd138177d5f4b7ee1eb63833360d227baa54f66d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072741"
---
# <a name="how-to-create-a-property-visual-basic"></a>Comment : créer une propriété (Visual Basic)

Vous devez placer une définition de propriété entre une `Property` instruction et une `End Property` instruction. Dans cette définition, vous définissez une `Get` procédure, une `Set` procédure ou les deux. Tout le code de la propriété se trouve dans ces procédures.  
  
 La `Get` procédure récupère la valeur de la propriété, et la `Set` procédure stocke une valeur. Si vous souhaitez que la propriété dispose d’un accès en lecture/écriture, vous devez définir les deux procédures. Pour une propriété en lecture seule, vous définissez uniquement `Get` , et pour une propriété en écriture seule, vous définissez uniquement `Set` .  
  
### <a name="to-create-a-property"></a>Pour créer une propriété  
  
1. En dehors d’une propriété ou d’une procédure, utilisez une [instruction Property](../../../language-reference/statements/property-statement.md), suivie d’une `End Property` instruction.  
  
2. Si la propriété accepte des paramètres, suivez le `Property` mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3. Suivez les parenthèses avec une `As` clause pour spécifier le type de données de la valeur de la propriété. Vous devez spécifier le type de données même pour une propriété en écriture seule.  
  
4. Ajoutez `Get` les `Set` procédures et, le cas échéant. Consultez les instructions suivantes.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Pour créer une procédure d’extraction qui récupère une valeur de propriété  
  
1. Entre les `Property` `End Property` instructions et, écrivez une [instruction d’extraction](../../../language-reference/statements/get-statement.md), suivie d’une `End Get` instruction. Vous n’avez pas besoin de définir de paramètres pour la `Get` procédure.  
  
2. Placez les instructions de code pour récupérer la valeur de la propriété entre les `Get` `End Get` instructions et. Ce code peut inclure d’autres calculs et manipulations de données en plus de la génération et du retour de la valeur de la propriété.  
  
3. Utilisez une `Return` instruction pour retourner la valeur de la propriété au code appelant.  
  
 Vous devez écrire une `Get` procédure pour une propriété en lecture-écriture et pour une propriété en lecture seule. Vous ne devez pas définir une `Get` procédure pour une propriété en écriture seule.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Pour créer une procédure Set qui écrit la valeur d’une propriété  
  
1. Entre les `Property` `End Property` instructions et, écrivez une [instruction Set](../../../language-reference/statements/set-statement.md), suivie d’une `End Set` instruction.  
  
2. Dans l' `Set` instruction, suivez le `Set` mot clé avec une liste de paramètres entre parenthèses. Cette liste de paramètres doit inclure au moins un paramètre de valeur pour la valeur passée par le code appelant. Le nom par défaut de ce paramètre de valeur est `Value` , mais vous pouvez utiliser un autre nom, le cas échéant. Le paramètre de valeur doit avoir le même type de données que la propriété elle-même.  
  
3. Placez les instructions de code pour stocker une valeur dans la propriété entre `Set` les `End Set` instructions et. Ce code peut inclure d’autres calculs et manipulations de données, en plus de la validation et du stockage de la valeur de la propriété.  
  
4. Utilisez le paramètre value pour accepter la valeur fournie par le code appelant. Vous pouvez soit stocker cette valeur directement dans une instruction d’assignation, soit l’utiliser dans une expression pour calculer la valeur interne à stocker.  
  
 Vous devez écrire une `Set` procédure pour une propriété en lecture-écriture et pour une propriété en écriture seule. Vous ne devez pas définir une `Set` procédure pour une propriété en lecture seule.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant crée une propriété en lecture/écriture qui stocke un nom complet comme deux noms constitutifs, le prénom et le nom. Lorsque le code appelant lit `fullName` , la `Get` procédure combine les deux noms constitutifs et retourne le nom complet. Lorsque le code appelant assigne un nouveau nom complet, la `Set` procédure tente de la décomposer en deux noms constitutifs. S’il ne trouve pas d’espace, il le stocke comme premier nom.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 L’exemple suivant montre des appels classiques aux procédures de propriété de `fullName` . Le premier appel définit la valeur de la propriété et le deuxième appel la récupère.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures Property](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Différences entre les propriétés et les variables en Visual Basic](./differences-between-properties-and-variables.md)
- [Comment : déclarer une propriété avec des niveaux d'accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Comment : obtenir une valeur d'une propriété](./how-to-get-a-value-from-a-property.md)
