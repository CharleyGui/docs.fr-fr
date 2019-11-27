---
title: 'Comment : créer une propriété'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: ee5a9f687765ce064eb3c3f84218ed36eb916d9d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349709"
---
# <a name="how-to-create-a-property-visual-basic"></a>Comment : créer une propriété (Visual Basic)
Vous devez placer une définition de propriété entre une instruction `Property` et une instruction `End Property`. Dans cette définition, vous définissez une procédure `Get`, une procédure `Set` ou les deux. Tout le code de la propriété se trouve dans ces procédures.  
  
 La procédure `Get` récupère la valeur de la propriété, et la procédure `Set` stocke une valeur. Si vous souhaitez que la propriété dispose d’un accès en lecture/écriture, vous devez définir les deux procédures. Pour une propriété en lecture seule, vous définissez uniquement `Get`, et pour une propriété en écriture seule, vous définissez uniquement `Set`.  
  
### <a name="to-create-a-property"></a>Pour créer une propriété  
  
1. En dehors d’une propriété ou d’une procédure, utilisez une [instruction Property](../../../../visual-basic/language-reference/statements/property-statement.md), suivie d’une instruction `End Property`.  
  
2. Si la propriété accepte des paramètres, suivez le mot clé `Property` avec le nom de la procédure, puis la liste de paramètres entre parenthèses.  
  
3. Suivez les parenthèses avec une clause `As` pour spécifier le type de données de la valeur de la propriété. Vous devez spécifier le type de données même pour une propriété en écriture seule.  
  
4. Ajoutez `Get` et `Set` procédures, le cas échéant. Consultez les instructions suivantes.  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a>Pour créer une procédure d’extraction qui récupère une valeur de propriété  
  
1. Entre les instructions `Property` et `End Property`, écrivez une [instruction d’extraction](../../../../visual-basic/language-reference/statements/get-statement.md), suivie d’une instruction de `End Get`. Vous n’avez pas besoin de définir de paramètres pour la procédure `Get`.  
  
2. Placez les instructions de code pour récupérer la valeur de la propriété entre les instructions `Get` et `End Get`. Ce code peut inclure d’autres calculs et manipulations de données en plus de la génération et du retour de la valeur de la propriété.  
  
3. Utilisez une instruction `Return` pour retourner la valeur de la propriété au code appelant.  
  
 Vous devez écrire une procédure `Get` pour une propriété en lecture-écriture et pour une propriété en lecture seule. Vous ne devez pas définir une procédure `Get` pour une propriété en écriture seule.  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a>Pour créer une procédure Set qui écrit la valeur d’une propriété  
  
1. Entre les instructions `Property` et `End Property`, écrivez une [instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md), suivie d’une instruction `End Set`.  
  
2. Dans l’instruction `Set`, suivez les parenthèses du mot clé `Set` avec une liste de paramètres. Cette liste de paramètres doit inclure au moins un paramètre de valeur pour la valeur passée par le code appelant. Le nom par défaut de ce paramètre de valeur est `Value`, mais vous pouvez utiliser un autre nom, le cas échéant. Le paramètre de valeur doit avoir le même type de données que la propriété elle-même.  
  
3. Placez les instructions de code pour stocker une valeur dans la propriété entre les instructions `Set` et `End Set`. Ce code peut inclure d’autres calculs et manipulations de données, en plus de la validation et du stockage de la valeur de la propriété.  
  
4. Utilisez le paramètre value pour accepter la valeur fournie par le code appelant. Vous pouvez soit stocker cette valeur directement dans une instruction d’assignation, soit l’utiliser dans une expression pour calculer la valeur interne à stocker.  
  
 Vous devez écrire une procédure `Set` pour une propriété en lecture-écriture et pour une propriété en écriture seule. Vous ne devez pas définir une procédure `Set` pour une propriété en lecture seule.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée une propriété en lecture/écriture qui stocke un nom complet comme deux noms constitutifs, le prénom et le nom. Lorsque le code appelant lit `fullName`, la procédure `Get` combine les deux noms constitutifs et retourne le nom complet. Lorsque le code appelant assigne un nouveau nom complet, la procédure `Set` tente de la décomposer en deux noms constitutifs. S’il ne trouve pas d’espace, il le stocke comme premier nom.  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 L’exemple suivant montre des appels classiques aux procédures de propriété de `fullName`. Le premier appel définit la valeur de la propriété et le deuxième appel la récupère.  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Procédures de propriété](./property-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Différences entre les propriétés et les variables dans Visual Basic](./differences-between-properties-and-variables.md)
- [Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Guide pratique : appeler une procédure de propriété](./how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)
- [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)
