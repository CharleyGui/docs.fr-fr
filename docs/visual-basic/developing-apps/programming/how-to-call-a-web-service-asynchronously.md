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
# <a name="how-to-call-a-web-service-asynchronously-visual-basic"></a><span data-ttu-id="5b137-102">Guide pratique pour appeler un service web de manière asynchrone (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b137-102">How to: Call a Web Service Asynchronously (Visual Basic)</span></span>

<span data-ttu-id="5b137-103">Cet exemple attache un gestionnaire à l'événement de gestionnaire asynchrone d'un service web pour qu'il puisse récupérer le résultat d'un appel de méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="5b137-103">This example attaches a handler to a Web service's asynchronous handler event, so that it can retrieve the result of an asynchronous method call.</span></span> <span data-ttu-id="5b137-104">Cet exemple utilise le service web DemoTemperatureService disponible sur `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="5b137-104">This example used the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span>

<span data-ttu-id="5b137-105">Quand vous faites référence à un service web dans votre projet dans l'IDE (Integrated Development Environment) de Visual Studio, il est ajouté à l'objet `My.WebServices` et l'IDE génère une classe proxy cliente pour accéder à un service web spécifié.</span><span class="sxs-lookup"><span data-stu-id="5b137-105">When you reference a Web service in your project in the Visual Studio Integrated Development Environment (IDE), it is added to the `My.WebServices` object, and the IDE generates a client proxy class to access a specified Web service</span></span>

<span data-ttu-id="5b137-106">La classe proxy vous permet d'appeler les méthodes du service web de manière synchrone (votre application attend que la fonction soit terminée).</span><span class="sxs-lookup"><span data-stu-id="5b137-106">The proxy class allows you to call the Web service methods synchronously, where your application waits for the function to complete.</span></span> <span data-ttu-id="5b137-107">De plus, le proxy crée des membres supplémentaires pour aider à appeler la méthode de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="5b137-107">In addition, the proxy creates additional members to help call the method asynchronously.</span></span> <span data-ttu-id="5b137-108">Pour chaque fonction du service web, *NameOfWebServiceFunction*, le proxy crée une sous-routine *NameOfWebServiceFunction*`Async`, un événement *NameOfWebServiceFunction*`Completed` et une classe *NameOfWebServiceFunction*`CompletedEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="5b137-108">For each Web service function, *NameOfWebServiceFunction*, the proxy creates a *NameOfWebServiceFunction*`Async` subroutine, a *NameOfWebServiceFunction*`Completed` event, and a *NameOfWebServiceFunction*`CompletedEventArgs` class.</span></span> <span data-ttu-id="5b137-109">Cet exemple montre comment utiliser les membres asynchrones pour accéder à la fonction `getTemp` du service web DemoTemperatureService.</span><span class="sxs-lookup"><span data-stu-id="5b137-109">This example demonstrates how to use the asynchronous members to access the `getTemp` function of the DemoTemperatureService Web service.</span></span>

> [!NOTE]
> <span data-ttu-id="5b137-110">Ce code ne fonctionne pas dans les applications web, car ASP.NET ne prend pas en charge l'objet `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="5b137-110">This code does not work in Web applications, because ASP.NET does not support the `My.WebServices` object.</span></span>

## <a name="call-a-web-service-asynchronously"></a><span data-ttu-id="5b137-111">Appeler un service Web de façon asynchrone</span><span class="sxs-lookup"><span data-stu-id="5b137-111">Call a Web service asynchronously</span></span>

1. <span data-ttu-id="5b137-112">Faites référence au service web DemoTemperatureService disponible sur `http://www.xmethods.net`.</span><span class="sxs-lookup"><span data-stu-id="5b137-112">Reference the DemoTemperatureService Web service at `http://www.xmethods.net`.</span></span> <span data-ttu-id="5b137-113">L'adresse est</span><span class="sxs-lookup"><span data-stu-id="5b137-113">The address is</span></span>

    ```http
    http://www.xmethods.net/sd/2001/DemoTemperatureService.wsdl
    ```

2. <span data-ttu-id="5b137-114">Ajoutez un gestionnaire d'événements pour l'événement `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="5b137-114">Add an event handler for the `getTempCompleted` event:</span></span>

    ```vb
    Private Sub getTempCompletedHandler(ByVal sender As Object,
        ByVal e As net.xmethods.www.getTempCompletedEventArgs)

        MsgBox("Temperature: " & e.Result)
    End Sub
    ```

    > [!NOTE]
    > <span data-ttu-id="5b137-115">Vous ne pouvez pas utiliser l'instruction `Handles` pour associer un gestionnaire d'événements aux événements de l'objet `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="5b137-115">You cannot use the `Handles` statement to associate an event handler with the `My.WebServices` object's events.</span></span>

3. <span data-ttu-id="5b137-116">Ajoutez un champ pour suivre si le gestionnaire d'événements a été ajouté à l'événement `getTempCompleted` :</span><span class="sxs-lookup"><span data-stu-id="5b137-116">Add a field to track if the event handler has been added to the `getTempCompleted` event:</span></span>

    ```vb
    Private handlerAttached As Boolean = False
    ```

4. <span data-ttu-id="5b137-117">Ajoutez une méthode pour ajouter le gestionnaire d'événements à l'événement `getTempCompleted`, si nécessaire, et pour appeler la méthode `getTempAsync` :</span><span class="sxs-lookup"><span data-stu-id="5b137-117">Add a method to add the event handler to the `getTempCompleted` event, if necessary, and to call the `getTempAsync` method:</span></span>

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

    <span data-ttu-id="5b137-118">Pour appeler la méthode web `getTemp` de manière asynchrone, appelez la méthode `CallGetTempAsync`.</span><span class="sxs-lookup"><span data-stu-id="5b137-118">To call the `getTemp` Web method asynchronously, call the `CallGetTempAsync` method.</span></span> <span data-ttu-id="5b137-119">Quand la méthode web se termine, sa valeur de retour est passée au gestionnaire d'événements `getTempCompletedHandler`.</span><span class="sxs-lookup"><span data-stu-id="5b137-119">When the Web method finishes, its return value is passed to the `getTempCompletedHandler` event handler.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b137-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b137-120">See also</span></span>

- [<span data-ttu-id="5b137-121">Accès aux services web d’une application</span><span class="sxs-lookup"><span data-stu-id="5b137-121">Accessing Application Web Services</span></span>](accessing-application-web-services.md)
- [<span data-ttu-id="5b137-122">My.WebServices (objet)</span><span class="sxs-lookup"><span data-stu-id="5b137-122">My.WebServices Object</span></span>](../../language-reference/objects/my-webservices-object.md)
