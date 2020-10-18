---
title: Visual Basic des messages d’erreur
titleSuffix: ''
ms.date: 10/13/2020
helpviewer_keywords:
- errors [Visual Basic]
- error messages
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 70973b6d34ed1a84a38af3694e144dfcefa61c20
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163374"
---
# <a name="error-messages-in-visual-basic"></a>Messages d’erreur dans Visual Basic

Lors de la compilation ou de l’exécution d’une application Visual Basic, les types d’erreurs suivants peuvent se produire :

- Erreurs au moment de la compilation, qui se produisent quand vous compilez une application.

- Erreurs d’exécution, qui se produisent lorsqu’une application est en cours d’exécution.

Pour plus d’informations sur la résolution d’une erreur spécifique, consultez la page [Ressources supplémentaires pour les programmeurs Visual Basic](../../getting-started/additional-resources.md).

## <a name="run-time-errors"></a>Erreurs d’exécution

Si une application Visual Basic tente d’exécuter une action que le système ne peut pas exécuter, une erreur d’exécution se produit et Visual Basic lève un <xref:System.Exception> objet. Visual Basic pouvez générer des erreurs personnalisées de tout type de données, y compris des `Exception` objets, à l’aide de l' `Throw` instruction. Une application peut identifier l’erreur en affichant le numéro d’erreur et le message d’une exception interceptée. Si l’erreur n’est pas interceptée, l’application se termine.

Le code peut intercepter et examiner les erreurs d’exécution. Si vous placez le code qui génère l’erreur dans un bloc `Try`, vous pouvez intercepter toute erreur levée dans un bloc `Catch` correspondant. Pour plus d’informations sur la façon d’intercepter les erreurs à l’exécution et d’y répondre dans votre code, consultez la page [Instruction Try...Catch...Finally](../statements/try-catch-finally-statement.md).

## <a name="compile-time-errors"></a>Erreurs au moment de la compilation

Si le compilateur Visual Basic rencontre un problème dans le code, une erreur de compilation se produit. Dans l’éditeur de code Visual Studio, vous pouvez facilement identifier la ligne de code à l’origine de l’erreur, car une ligne ondulée apparaît sous cette ligne de code. Le message d’erreur s’affiche si vous pointez sur la ligne ondulée ou ouvrez la **Liste d’erreurs**, qui affiche également les autres messages.

Si un identificateur a un trait de soulignement ondulé et un trait de soulignement bref s’affiche sous le caractère le plus à droite, vous pouvez générer un stub pour la classe, le constructeur, la méthode, la propriété, le champ ou l’énumération. Pour plus d’informations, consultez [générer à partir de l’utilisation (Visual Studio)](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).

En résolvant les avertissements du compilateur Visual Basic, vous pourrez écrire du code qui s’exécute plus rapidement et présente moins de bogues. Ces avertissements identifient le code susceptible de provoquer des erreurs lors de l’exécution de l’application. Par exemple, le compilateur vous avertit si vous tentez d’appeler un membre d’une variable objet non affectée, de retourner une valeur à partir d’une fonction sans définir la valeur renvoyée, ou d’exécuter un bloc `Try` contenant des erreurs dans la logique d’interception des exceptions. Pour plus d’informations sur les avertissements, et pour savoir comment les activer et les désactiver, consultez la page [Configurer les avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).
