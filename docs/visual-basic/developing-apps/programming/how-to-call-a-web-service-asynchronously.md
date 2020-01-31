---
title: 'Comment : appeler un service Web de manière asynchrone'
ms.date: 07/20/2015
helpviewer_keywords:
- asynchronous calls [Visual Basic]
- Web services [Visual Basic], accessing
ms.assetid: ff8046f4-f1f2-4d8b-90b7-95e3f7415418
ms.openlocfilehash: d288cc1f2991a8f504dc9f1b206bba76fa378b75
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794562"
---
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a>Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)

Cet exemple attache un gestionnaire à l'événement de gestionnaire asynchrone d'un service web pour qu'il puisse récupérer le résultat d'un appel de méthode asynchrone. Cet exemple utilise le service web DemoTemperatureService disponible sur `http://www.xmethods.net`.

Quand vous faites référence à un service web dans votre projet dans l'IDE (Integrated Development Environment) de Visual Studio, il est ajouté à l'objet `My.WebServices` et l'IDE génère une classe proxy cliente pour accéder à un service web spécifié.

La classe proxy vous permet d'appeler les méthodes du service web de manière synchrone (votre application attend que la fonction soit terminée). De plus, le proxy crée des membres supplémentaires pour aider à appeler la méthode de manière asynchrone. Pour chaque fonction du service web, *NameOfWebServiceFunction*, le proxy crée une sous-routine *NameOfWebServiceFunction*`Async`, un événement *NameOfWebServiceFunction*`Completed` et une classe *NameOfWebServiceFunction*`CompletedEventArgs`. Cet exemple montre comment utiliser les membres asynchrones pour accéder à la fonction `getTemp` du service web DemoTemperatureService.

> [!NOTE]
> Ce code ne fonctionne pas dans les applications web, car ASP.NET ne prend pas en charge l'objet `My.WebServices`.

## <a name="call-a-web-service-asynchronously"></a>Appeler un service Web de façon asynchrone

1. Faites référence au service web DemoTemperatureService disponible sur `http://www.xmethods.net`. L'adresse est

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. Ajoutez un gestionnaire d'événements pour l'événement `getTempCompleted` :

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > Vous ne pouvez pas utiliser l'instruction `Handles` pour associer un gestionnaire d'événements aux événements de l'objet `My.WebServices`.

3. Ajoutez un champ pour suivre si le gestionnaire d'événements a été ajouté à l'événement `getTempCompleted` :

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. Ajoutez une méthode pour ajouter le gestionnaire d'événements à l'événement `getTempCompleted`, si nécessaire, et pour appeler la méthode `getTempAsync` :

    ```vb
    Sub CallGetTempAsync(ByVal zipCode As Integer)
        If Not handlerAttached Then
            AddHandler My.WebServices.
                TemperatureService.getTempCompleted,
                AddressOf Me.TS_getTempCompleted
            handlerAttached = True
        End If
        My.WebServices.TemperatureService.getTempAsync(zipCode)
    End Sub
    ```

    Pour appeler la méthode web `getTemp` de manière asynchrone, appelez la méthode `CallGetTempAsync`. Quand la méthode web se termine, sa valeur de retour est passée au gestionnaire d'événements `getTempCompletedHandler`.

## <a name="see-also"></a>Voir aussi

- [Accès aux services web d’une application](accessing-application-web-services.md)
- [My.WebServices (objet)](../../language-reference/objects/my-webservices-object.md)
