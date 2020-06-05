---
title: Procédures
ms.date: 04/28/2017
helpviewer_keywords:
- procedures [Visual Basic], structured code
- Visual Basic code, procedures
- procedures [Visual Basic], types of
- structured code [Visual Basic], procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
ms.openlocfilehash: c0d9921704570c6984b203817aed8f5546b2f936
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408788"
---
# <a name="procedures-in-visual-basic"></a>Procédures dans Visual Basic
Une *procédure* est un bloc de Visual Basic instructions encadrées par une instruction de déclaration ( `Function` , `Sub` ,, `Operator` `Get` , `Set` ) et une `End` déclaration correspondante. Toutes les instructions exécutables dans Visual Basic doivent se trouver dans une procédure.  
  
## <a name="calling-a-procedure"></a>Appel d’une procédure  
 Vous appelez une procédure à partir d’une autre partie du code. Il s’agit d’un *appel de procédure*. Une fois la procédure exécutée, elle renvoie le contrôle au code qui l’a appelée, opération qui se nomme *appel du code*. Le code appelant est une instruction ou une expression au sein d’une instruction, qui désigne la procédure par nom et lui transfère le contrôle.  
  
## <a name="returning-from-a-procedure"></a>Retour d’une procédure  
 Une procédure retourne le contrôle au code appelant lorsqu’elle est terminée. Pour ce faire, il peut utiliser une [instruction return](../../../language-reference/statements/return-statement.md), l’instruction de [sortie](../../../language-reference/statements/exit-statement.md) appropriée pour la procédure ou l’instruction [end de \<keyword> ](../../../language-reference/statements/end-keyword-statement.md) la procédure. Le contrôle passe ensuite au code appelant après le point de l’appel de procédure.  
  
- Avec une instruction `Return`, le contrôle retourne immédiatement au code appelant. Les instructions qui suivent l’instruction `Return` ne s’exécutent pas. Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.  
  
- Avec une instruction `Exit Sub` ou `Exit Function`, le contrôle retourne immédiatement au code appelant. Les instructions qui suivent l’instruction `Exit` ne s’exécutent pas. Vous pouvez utiliser plusieurs instructions `Exit` dans la même procédure et combiner des instructions `Return` et `Exit` dans la même procédure.  
  
- Si une procédure ne comporte pas d’instructions `Return` ou `Exit`, elle se termine par une instruction `End Sub` ou `End Function`, `End Get`, ou l’instruction `End Set` qui suit la dernière instruction du corps de la procédure. L’instruction `End` retourne immédiatement le contrôle au code appelant. Une procédure ne peut contenir qu’une seule instruction `End`.  
  
## <a name="parameters-and-arguments"></a>Paramètres et arguments  
 Dans la plupart des cas, une procédure doit s’exécuter sur des données différentes chaque fois que vous l’appelez. Vous pouvez transmettre ces informations à la procédure dans le cadre de l’appel de procédure. La procédure définit zéro ou plusieurs *paramètres*, chacun d’eux représentant une valeur qu’elle s’attend à recevoir de votre part. Dans l’appel de procédure, un *argument* est associé à chaque paramètre dans la définition de la procédure. Un argument représente la valeur que vous passez au paramètre correspondant dans un appel de procédure donné.  
  
## <a name="types-of-procedures"></a>Types de procédures  
 Visual Basic utilise plusieurs types de procédures :  
  
- Les [procédures Sub](./sub-procedures.md) exécutent des actions mais ne retournent aucune valeur au code appelant.  
  
- Les procédures de gestion d’événements sont des procédures `Sub` qui s’exécutent en réponse à un événement déclenché par une action de l’utilisateur ou une occurrence dans un programme.  
  
- Les [procédures Function](./function-procedures.md) retournent une valeur au code appelant. Elles peuvent effectuer d’autres actions avant de retourner une valeur.

    Certaines fonctions écrites en langage C# retournent une *valeur de retour de référence*. Les appelants de fonction peuvent modifier la valeur de retour, et cette modification est répercutée dans l’état de l’objet appelé. À partir de Visual Basic 2017, le code Visual Basic peut consommer des valeurs de retour de référence, même s’il ne peut pas retourner une valeur par référence. Pour plus d’informations, consultez [Valeurs de retour de référence](ref-return-values.md).
  
- Les [procédures Property](./property-procedures.md) renvoient et attribuent des valeurs de propriétés à des objets ou modules.  
  
- Les [procédures Operator](./operator-procedures.md) définissent le comportement d’un opérateur standard lorsqu’un ou les deux opérandes représentent une structure ou classe qui vient d’être définie.  
  
- Les [procédures génériques dans Visual Basic](../data-types/generic-procedures.md) définissent un ou plusieurs *paramètres de type* en plus de leurs paramètres normaux, et le code appelant peut donc passer des types de données spécifiques chaque fois qu’il effectue un appel.  
  
## <a name="procedures-and-structured-code"></a>Procédures et code structuré  
 Chaque ligne de code exécutable dans votre application doit figurer à l’intérieur d’une procédure, par exemple `Main`, `calculate`, ou `Button1_Click`. Si vous décomposez des procédures complexes en procédures plus simples, votre application devient plus lisible.  
  
 Les procédures sont utiles pour effectuer des tâches répétitives ou partagées, notamment des calculs fréquemment utilisés, la manipulation de texte et de contrôle et les opérations dans des bases de données. Vous pouvez appeler une procédure à partir de différentes sections de votre code et ainsi utiliser les procédures comme des blocs de construction pour votre application.  
  
 Structurer votre code avec des procédures vous offre les avantages suivants :  
  
- Les procédures vous permettent de décomposer vos programmes en unités logiques discrètes. Vous pouvez déboguer des unités distinctes plus facilement qu’en déboguant un programme entier sans procédure.  
  
- Après avoir développé des procédures pour les utiliser dans un programme, vous pouvez les utiliser dans d’autres programmes, avec peu ou pas de modifications. Cela vous évite une duplication de code.  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique : créer une procédure](./how-to-create-a-procedure.md)
- [Sub, procédures](./sub-procedures.md)
- [Function, procédures](./function-procedures.md)
- [Procédures Property](./property-procedures.md)
- [Procédures d'opérateur](./operator-procedures.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Procédures récursives](./recursive-procedures.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Generic Procedures in Visual Basic](../data-types/generic-procedures.md)
- [Objets et classes](../objects-and-classes/index.md)
