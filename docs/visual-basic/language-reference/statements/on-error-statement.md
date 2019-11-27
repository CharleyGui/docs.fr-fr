---
title: On Error, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: d62c2ba1849b7015ed877d503220026a2dfeff57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353816"
---
# <a name="on-error-statement-visual-basic"></a>On Error, instruction (Visual Basic)
Active une routine de gestion des erreurs et spécifie l’emplacement de la routine dans une procédure. peut également être utilisé pour désactiver une routine de gestion des erreurs. L’instruction `On Error` est utilisée dans la gestion non structurée des erreurs et peut être utilisée à la place de la gestion structurée des exceptions. La [gestion structurée des exceptions](../../../standard/exceptions/index.md) étant intégrée à .net, est généralement plus efficace, et est donc recommandée lors de la gestion des erreurs d’exécution dans votre application.

 Sans la gestion des erreurs ou la gestion des exceptions, toute erreur d’exécution qui se produit est fatale : un message d’erreur s’affiche et l’exécution s’arrête.

> [!NOTE]
> Le mot clé `Error` est également utilisé dans l' [instruction Error](../../../visual-basic/language-reference/statements/error-statement.md), qui est prise en charge pour la compatibilité descendante.

## <a name="syntax"></a>Syntaxe

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Composants

|Terme|Définition|
|---|---|
|`GoTo` la *ligne*|Active la routine de gestion des erreurs qui démarre à la ligne spécifiée dans l’argument de *ligne* requis. L’argument de *ligne* est une étiquette de ligne ou un numéro de ligne. Si une erreur d’exécution se produit, le contrôle effectue une branche vers la ligne spécifiée, ce qui rend le gestionnaire d’erreurs actif. La ligne spécifiée doit être dans la même procédure que l’instruction `On Error` ou une erreur de compilation se produit.|
|`GoTo 0`|Désactive le gestionnaire d’erreurs activé dans la procédure actuelle et le réinitialise à `Nothing`.|
|`GoTo -1`|Désactive l’exception activée dans la procédure actuelle et la réinitialise à `Nothing`.|
|`Resume Next`|Spécifie que lorsqu’une erreur d’exécution se produit, le contrôle passe à l’instruction qui suit immédiatement l’instruction où l’erreur s’est produite, et l’exécution se poursuit à partir de ce point. Utilisez ce formulaire plutôt que `On Error GoTo` lors de l’accès aux objets.|

## <a name="remarks"></a>Notes

> [!NOTE]
> Nous vous recommandons d’utiliser la gestion structurée des exceptions dans votre code dans la mesure du possible, au lieu d’utiliser la gestion des exceptions non structurées et l’instruction `On Error`. Pour plus d’informations, consultez [Try...Catch...Finally, instruction](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

 Un gestionnaire d’erreurs « activé » est activé par une instruction `On Error`. Un gestionnaire d’erreurs « actif » est un gestionnaire activé qui est en train de gérer une erreur.

 Si une erreur se produit alors qu’un gestionnaire d’erreurs est actif (entre l’occurrence de l’erreur et une instruction `Resume`, `Exit Sub`, `Exit Function`ou `Exit Property`), le gestionnaire d’erreurs de la procédure en cours ne peut pas gérer l’erreur. Le contrôle retourne à la procédure appelante.
  
 Si la procédure appelante a un gestionnaire d’erreurs activé, elle est activée pour gérer l’erreur. Si le gestionnaire d’erreurs de la procédure appelante est également actif, le contrôle passe par les procédures appelées précédentes jusqu’à ce qu’un gestionnaire d’erreurs activé, mais inactif soit trouvé. Si aucun gestionnaire d’erreurs de ce type n’est trouvé, l’erreur est irrécupérable au point où elle s’est réellement produite.
  
 Chaque fois que le gestionnaire d’erreurs repasse le contrôle à une procédure appelante, cette procédure devient la procédure en cours. Une fois qu’une erreur est gérée par un gestionnaire d’erreurs dans une procédure, l’exécution reprend dans la procédure en cours au point désigné par l’instruction `Resume`.
  
> [!NOTE]
> Une routine de gestion des erreurs n’est pas une procédure `Sub` ou `Function`. Il s’agit d’une section de code marquée par une étiquette de ligne ou un numéro de ligne.
  
## <a name="number-property"></a>Number, propriété
 Les routines de gestion des erreurs reposent sur la valeur de la propriété `Number` de l’objet `Err` pour déterminer la cause de l’erreur. La routine doit tester ou enregistrer les valeurs de propriété pertinentes dans l’objet `Err` avant qu’une autre erreur ne se produise ou qu’une procédure susceptible de provoquer une erreur soit appelée. Les valeurs de propriété dans l’objet `Err` reflètent uniquement l’erreur la plus récente. Le message d’erreur associé à `Err.Number` est contenu dans `Err.Description`.  
  
## <a name="throw-statement"></a>Throw, instruction  
 Une erreur levée avec la méthode `Err.Raise` affecte à la propriété `Exception` une instance nouvellement créée de la classe <xref:System.Exception>. Afin de prendre en charge le déclenchement d’exceptions de types d’exception dérivés, une instruction `Throw` est prise en charge dans le langage. Cela prend un paramètre unique qui est l’instance d’exception à lever. L’exemple suivant montre comment ces fonctionnalités peuvent être utilisées avec la prise en charge de la gestion des exceptions existante :

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Notez que l’instruction `On Error GoTo` intercepte toutes les erreurs, quelle que soit la classe d’exception.
  
## <a name="on-error-resume-next"></a>En cas d’erreur, reprendre la prochaine
 `On Error Resume Next` fait en sorte que l’exécution continue avec l’instruction qui suit immédiatement l’instruction qui a provoqué l’erreur d’exécution, ou avec l’instruction qui suit immédiatement l’appel le plus récent de la procédure contenant l’instruction `On Error Resume Next`. Cette instruction permet à l’exécution de continuer en dépit d’une erreur d’exécution. Vous pouvez placer la routine de gestion des erreurs dans laquelle l’erreur se produit au lieu de transférer le contrôle à un autre emplacement de la procédure. Une instruction `On Error Resume Next` devient inactive lorsqu’une autre procédure est appelée. vous devez donc exécuter une instruction `On Error Resume Next` dans chaque routine appelée si vous souhaitez une gestion des erreurs Inline au sein de cette routine.
  
> [!NOTE]
> La construction `On Error Resume Next` peut être préférable à `On Error GoTo` lors de la gestion des erreurs générées au cours de l’accès à d’autres objets. La vérification de `Err` après chaque interaction avec un objet supprime l’ambiguïté relative à l’objet auquel le code a accédé. Vous pouvez vous assurer que l’objet a placé le code d’erreur dans `Err.Number`, ainsi que l’objet qui a généré l’erreur à l’origine (l’objet spécifié dans `Err.Source`).

## <a name="on-error-goto-0"></a>En cas d’erreur GoTo 0
 `On Error GoTo 0` désactive la gestion des erreurs dans la procédure actuelle. Elle ne spécifie pas la ligne 0 comme début du code de gestion des erreurs, même si la procédure contient une ligne numérotée 0. Sans instruction `On Error GoTo 0`, un gestionnaire d’erreurs est automatiquement désactivé lorsqu’une procédure est quittée.

## <a name="on-error-goto--1"></a>En cas d’erreur GoTo-1
 `On Error GoTo -1` désactive l’exception dans la procédure actuelle. Elle ne spécifie pas la ligne-1 comme début du code de gestion des erreurs, même si la procédure contient une ligne numérotée-1. Sans instruction `On Error GoTo -1`, une exception est automatiquement désactivée lors de la fermeture d’une procédure.

 Pour empêcher l’exécution du code de gestion des erreurs quand aucune erreur ne s’est produite, placez une instruction `Exit Sub`, `Exit Function`ou `Exit Property` immédiatement avant la routine de gestion des erreurs, comme dans le fragment suivant :

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 Ici, le code de gestion des erreurs suit l’instruction `Exit Sub` et précède l’instruction `End Sub` pour la séparer du déroulement de la procédure. Vous pouvez placer le code de gestion des erreurs n’importe où dans une procédure.

## <a name="untrapped-errors"></a>Erreurs ininterrompues
 Les erreurs non interceptées dans les objets sont retournées à l’application de contrôle lorsque l’objet s’exécute en tant que fichier exécutable. Dans l’environnement de développement, les erreurs qui ne sont pas interceptées sont retournées à l’application de contrôle uniquement si les options appropriées sont définies. Consultez la documentation de votre application hôte pour obtenir une description des options qui doivent être définies pendant le débogage, la façon de les définir et si l’hôte peut créer des classes.

 Si vous créez un objet qui accède à d’autres objets, vous devez tenter de gérer toutes les erreurs non gérées qu’ils passent. Si ce n’est pas le cas, mappez les codes d’erreur dans `Err.Number` à l’une de vos erreurs, puis repassez-les à l’appelant de votre objet. Vous devez spécifier votre erreur en ajoutant votre code d’erreur à la constante `VbObjectError`. Par exemple, si votre code d’erreur est 1052, attribuez-le comme suit :

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Les erreurs système au cours des appels aux bibliothèques de liens dynamiques (dll) Windows ne déclenchent pas d’exceptions et ne peuvent pas être interceptées avec Visual Basic l’interception des erreurs. Lors de l’appel de fonctions DLL, vous devez vérifier la réussite ou l’échec de chaque valeur de retour (en fonction des spécifications de l’API) et, en cas de défaillance, vérifier la valeur dans la propriété `LastDLLError` de l’objet `Err`.

## <a name="example"></a>Exemple
 Cet exemple utilise d’abord l’instruction `On Error GoTo` pour spécifier l’emplacement d’une routine de gestion des erreurs au sein d’une procédure. Dans l’exemple, une tentative de division par zéro génère le numéro d’erreur 6. L’erreur est gérée dans la routine de gestion des erreurs et le contrôle est ensuite renvoyé à l’instruction qui a provoqué l’erreur. L’instruction `On Error GoTo 0` désactive l’interception des erreurs. L’instruction `On Error Resume Next` est ensuite utilisée pour différer l’interception des erreurs de manière à ce que le contexte de l’erreur générée par l’instruction suivante puisse être déterminé. Notez que `Err.Clear` est utilisé pour effacer les propriétés de l’objet `Err` une fois l’erreur gérée.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>Configuration requise
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)

 **Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit (instruction)](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Messages d’erreur](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally (instruction)](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
