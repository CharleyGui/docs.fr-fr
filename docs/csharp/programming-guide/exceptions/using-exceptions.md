---
title: Utilisation d'exceptions - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: a00259dfd5634ad9b9c951c3cd76da97afe5077d
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241693"
---
# <a name="use-exceptions-c-programming-guide"></a>Utiliser des exceptions (Guide de programmation C#)

En C#, les erreurs qui se produisent dans le programme au moment de l’exécution sont propagées à travers le programme à l’aide du mécanisme des exceptions. Les exceptions sont levées par le code qui rencontre une erreur et interceptées par le code qui peut corriger l’erreur. Les exceptions peuvent être levées par le Runtime .NET ou par le code d’un programme. Une fois qu’une exception est levée, elle se propage jusqu’en haut de la pile des appels, jusqu’à ce qu’une instruction `catch` soit trouvée pour l’exception. Les exceptions non interceptées sont gérées par un gestionnaire d’exceptions génériques fourni par le système qui affiche une boîte de dialogue.  
  
 Les exceptions sont représentées par des classes dérivées de <xref:System.Exception>. Cette classe identifie le type d’exception et contient des propriétés comportant des détails sur l’exception. Lever une exception implique de créer une instance d’une classe dérivée d’une exception, de configurer éventuellement les propriétés de l’exception, puis de lever l’objet à l’aide du mot clé `throw`. Par exemple :  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Après la levée d’une exception, le runtime vérifie l’instruction actuelle pour voir si elle se trouve dans un bloc `try`. Si tel est le cas, tous les blocs `catch` associés au bloc `try` font l’objet d’un contrôle permettant de déterminer s’ils peuvent intercepter l’exception. Les blocs `Catch` spécifient généralement des types d’exception ; si le type du bloc `catch` est identique à celui de l’exception ou d’une classe de base de l’exception, le bloc `catch` peut gérer la méthode. Par exemple :  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Si l’instruction qui lève une exception ne se trouve pas à l’intérieur d’un bloc `try` ou si le bloc `try` qui la contient n’a pas de bloc `catch` correspondant, le runtime vérifie que la méthode d’appel dispose d’une instruction `try` et de blocs `catch`. Le runtime continue jusqu’à la pile appelante, à la recherche d’un bloc `catch` compatible. Une fois le bloc `catch` trouvé et exécuté, le contrôle est passé à l’instruction suivante après le bloc `catch`.  
  
 Une instruction `try` peut contenir plusieurs blocs `catch`. La première instruction `catch` qui peut gérer l’exception est exécutée ; toutes les instructions `catch` suivantes, même compatibles, sont ignorées. Par conséquent, les blocs catch doivent toujours être classés du plus spécifique (ou du plus dérivé) au moins spécifique. Par exemple :  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Avant que le bloc `catch` ne soit exécuté, le runtime vérifie la présence de blocs `finally`. Les blocs `Finally` permettent au programmeur de nettoyer tout état ambigu qui pourrait subsister après l’abandon d’un bloc `try`, ou de libérer les ressources externes (telles que les handles graphiques, les connexions de bases de données ou les flux de fichiers) sans attendre que le garbage collector du runtime ne finalise les objets. Par exemple :  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Si `WriteByte()` a levé une exception, le code du deuxième bloc `try` qui essaie de rouvrir le fichier échoue si `file.Close()` n’est pas appelé, et le fichier reste verrouillé. Étant donné que les blocs `finally` sont exécutés même si une exception est levée, le bloc `finally` de l’exemple précédent autorise la fermeture correcte du fichier et permet d’éviter une erreur.  
  
 Si aucun bloc `catch` compatible n’est trouvé sur la pile des appels après la levée d’une exception, l’une des trois situations suivantes se produit :  
  
- Si l’exception se trouve dans un finaliseur, le finaliseur est abandonné et le finaliseur de base, le cas échéant, est appelé.  
  
- Si la pile des appels contient un constructeur statique ou un initialiseur de champ statique, une <xref:System.TypeInitializationException> est levée, avec l’exception d’origine assignée à la propriété <xref:System.Exception.InnerException%2A> de la nouvelle exception.  
  
- Si le début du thread est atteint, le thread est terminé.  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Exceptions et gestion des exceptions](./index.md)
