---
title: messages d'erreur
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 15d12802c92e7b9ed99c83885bd38e381c8b687d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353712"
---
# <a name="error-messages-visual-basic"></a>Messages d'erreur (Visual Basic)
Lorsque vous écrivez, compilez ou exécutez une application Visual Basic, les types d’erreurs suivants peuvent se produire :  
  
1. Erreurs au moment du design, qui se produisent lors de l’écriture d’une application dans Visual Studio.  
  
2. Erreurs de compilation qui se produisent lors de la compilation d’une application dans Visual Studio ou une invite de commandes.  
  
3. Erreurs d’exécution, qui se produisent lors de l’exécution d’une application dans Visual Studio ou en tant que fichier exécutable autonome.  
  
 Pour plus d’informations sur la résolution d’une erreur spécifique, consultez la page [Ressources supplémentaires pour les programmeurs Visual Basic](../../../visual-basic/getting-started/additional-resources.md).  
  
## <a name="run-time-errors"></a>Erreurs d’exécution  
 If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an `Exception` object. Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement. Une application peut identifier l’erreur en affichant le numéro d’erreur et le message d’une exception interceptée. Si l’erreur n’est pas interceptée, l’application se termine.  
  
 Le code peut intercepter et examiner les erreurs d’exécution. Si vous placez le code qui génère l’erreur dans un bloc `Try`, vous pouvez intercepter toute erreur levée dans un bloc `Catch` correspondant. Pour plus d’informations sur la façon d’intercepter les erreurs à l’exécution et d’y répondre dans votre code, consultez la page [Instruction Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="compile-time-errors"></a>Erreurs au moment de la compilation  
 Si le compilateur Visual Basic rencontre un problème dans le code, une erreur de compilation se produit. Dans l’éditeur de code, vous pouvez facilement identifier la ligne de code qui a provoqué l’erreur, car une ligne ondulée apparaît dessous. Le message d’erreur s’affiche si vous pointez sur la ligne ondulée ou ouvrez la **Liste d’erreurs**, qui affiche également les autres messages.  
  
 Si un identificateur a une ligne ondulée et qu’un trait de soulignement court apparaît sous le caractère le plus à droite, vous pouvez générer un stub pour la classe, le constructeur, la méthode, la propriété, le champ ou l’enum. Pour plus d’informations, consultez la page [Générer à partir de l’utilisation](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).
  
 En résolvant les avertissements du compilateur Visual Basic, vous pourrez écrire du code qui s’exécute plus rapidement et présente moins de bogues. Ces avertissements identifient le code susceptible de provoquer des erreurs lors de l’exécution de l’application. Par exemple, le compilateur vous avertit si vous tentez d’appeler un membre d’une variable objet non affectée, de retourner une valeur à partir d’une fonction sans définir la valeur renvoyée, ou d’exécuter un bloc `Try` contenant des erreurs dans la logique d’interception des exceptions. Pour plus d’informations sur les avertissements, et pour savoir comment les activer et les désactiver, consultez la page [Configurer les avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
